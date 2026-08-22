# Load Testing & Performance Baselines

## What Is This?
Load testing is the practice of simulating real-world user traffic to measure how your system performs under pressure. Think of it like stress-testing a bridge: before opening it to the public, engineers load it with weights far beyond expected traffic to ensure it won’t collapse. For software, this means pushing your API, database, or server to its limits to find breaking points *before* users do. Performance baselines are the measurable targets (e.g., "handle 1,000 requests/second with <200ms latency") that act as a "passing grade" for your system’s health.

## How It Works Internally
We’ll break this into four layers, using a restaurant analogy where your system is a kitchen:

### Layer 1: Minimum Viable Test (The Quiet Breakfast Rush)
```text
# Simulate 10 users ordering toast simultaneously
# Goal: Ensure basic concurrency works
# Tools: Simple scripts mimicking user actions
# Metrics: Did all orders complete? How long?
```
**Mechanics**: Tools like Python’s `locust` or `k6` generate virtual users ("toasters") sending requests to your API. Each user runs a predefined task (e.g., "fetch user profile"). The test measures response times and failures.

### Layer 2: Why Simple Tests Break (The Lunch Crowd Overwhelms)
```text
# 100 users arrive at once → kitchen chaos
# Database connections exhaust → "Order lost" errors
# Latency spikes to 10s for late orders
# Simple tests miss: resource exhaustion under scale
```
**Failure Condition**: Without limits, tests may not reveal bottlenecks like database connection pools or memory leaks. Real systems collapse under sustained load, not just brief spikes.

### Layer 3: Production-Grade Testing (The Dinner Service Drill)
```text
# 1,000 concurrent users with sustained load
# Mix of read/write operations (e.g., 70% menu views, 30% orders)
# Thresholds: "p99 latency < 500ms" or "0% errors"
# Tools: Locust (Python) or k6 (JavaScript) for realistic scenarios
```
**Production Additions**:  
- **Scenarios**: Simulate user behavior (e.g., "80% of users browse, 20% checkout").  
- **Thresholds**: Fail tests if metrics (e.g., p99 latency) exceed limits.  
- **Ramp-up**: Gradually increase users to mimic traffic growth.  

### Layer 4: Edge Cases (The Holiday Rush & Power Outage)
**Edge Case 1: Traffic Spike**  
*Trigger*: A viral post sends 10x traffic in 60 seconds.  
*Symptom*: Auto-scaling lags; 50% errors for 2 minutes.  
*Fix*: Test with rapid ramp-up (e.g., 0→10,000 users in 1 minute).  

**Edge Case 2: Soak Test**  
*Trigger*: 24-hour sustained load.  
*Symptom*: Memory leak crashes servers at hour 18.  
*Fix*: Run long-duration tests to catch resource leaks.

**CORE INSIGHT**: Load testing moves bottlenecks from "unknown failures in production" to "actionable fixes in staging." Baselines prevent regressions as your system evolves.

---

## Syntax and Structure
### Locust Load Test Script (Python)
```python
from locust import HttpUser, task, between

class WebsiteUser(HttpUser):
    wait_time = between(1, 5)  # Users wait 1-5 sec between actions

    @task
    def browse_menu(self):
        self.client.get("/menu")  # Simulate viewing menu

    @task(3)  # 3x more likely than other tasks
    def place_order(self):
        self.client.post("/order", json={"item": "burger"})
```
**Key Elements**:  
- `HttpUser`: Defines a virtual user type.  
- `@task`: Actions users perform (weighted by `@task(3)`).  
- `wait_time`: Realistic delays between requests.  
- Run with: `locust -f locustfile.py` → opens web UI to control tests.

---

## Practical Example
**Test an API Endpoint with Locust**  
Install: `pip install locust`  
Save as `locustfile.py`:
```python
from locust import HttpUser, task

class ApiUser(HttpUser):
    @task
    def get_data(self):
        self.client.get("/api/data")  # Target endpoint
```
Run: `locust -f locustfile.py` → Access UI at `http://localhost:8089`.  
Start 100 users, 10 spawn rate. Monitor:  
- **Requests/sec**: Throughput (RPS).  
- **p99**: Worst 1% of response times.  
- **Failures**: Errors under load.

---

## How This Connects to the Project
**BEFORE**: Your Secure API Gateway handles 10 requests/second in development. Untested, it crashes at 50 RPS during a demo.  
**AFTER**: Load tests reveal it sustains 500 RPS with p99 < 300ms after optimizing database queries.  
**File**: `tests/load/gateway_load.py` (Locust scripts).  
**Real-World Use**: Companies like Netflix run load tests daily to ensure streaming services survive traffic surges during events.

---

## Common Mistakes Beginners Make
1. **Ignoring p99 Latency**  
   Wrong idea: "Average response time is 100ms → we’re fine!"  
   Reality: p99 could be 2,000ms, meaning 1% of users wait 2 seconds. This kills user retention.

2. **Silent Resource Leaks**  
   Wrong code:  
   ```python
   @task
   def fetch_data(self):
       # Missing connection cleanup
       self.client.get("/data?heavy_query=true")  # Leaks DB connections
   ```  
   Under load, this exhausts database connections → 503 errors. Fix: Use connection pooling.

3. **Testing Too Late**  
   Waiting until production to load test → emergency fixes under pressure. Test in staging to avoid 3 AM incidents.

4. **Missing Thresholds**  
   Forgetting to set thresholds like "max 1% errors" → tests pass despite critical failures.

5. **Interview Question**  
   *"How would you diagnose a 500 error spike during a load test?"*  
   **Surface Answer**: "Check logs for timeouts or exceptions."  
   **Production Answer**: "Compare p95 latency to normal, check DB connection counts, and analyze garbage collection pauses in profiling tools."

---

## Verification Task 1: Debug This
**Symptom**: Your API’s p99 latency jumps to 10s at 100 RPS, but dev tests showed 200ms.  
**Evidence**: Database CPU at 95% during test.  
**Diagnose and Fix**:  
**Solution 1**:  
1. The bottleneck is the database, not the API code.  
2. Add an index to the queried table column.  
3. Implement query caching for frequent reads.  

---

## Verification Task 2: Design Decision
**Scenario**: Your team knows Python but needs CI-friendly load testing. Choose between **Locust** and **k6**.  
**Defend Your Choice**:  
**Solution 2**:  
Choose Locust if your team already uses Python (easier scripting). Choose k6 for JavaScript/CI pipelines (faster execution, built-in cloud integration). For Python projects, Locust reduces context-switching.

---

## Verification Task 3: Code Review
**Find the Bug**:  
```python
from locust import HttpUser, task

class User(HttpUser):
    @task
    def login(self):
        self.client.post("/login", json={"user": "test"})
        # Bug below
    def logout(self):
        self.client.post("/logout")  # Not a @task → never runs!
```
**Solution 3**:  
The `logout` method lacks the `@task` decorator. Under load, users never log out, causing session leaks. Fix: Add `@task` to `logout`.

---

## What Comes Next
**Linear Algebra** follows logically because analyzing load test data (e.g., identifying patterns in latency spikes) requires matrix operations and statistical models. Concepts like eigenvectors help reduce dimensionality in large performance datasets, making insights actionable.

---

## Reference Summary
Load testing simulates user traffic to identify performance bottlenecks before deployment, using tools like Locust (Python) or k6 (JavaScript). Key metrics include percentiles (p99 latency) and throughput (RPS), which define Service Level Agreements (SLAs). Tests must run in pre-production environments to catch issues like database leaks or scaling failures. Setting SLAs early (e.g., "p99 < 500ms at 100 RPS") ensures systems meet user expectations. This practice is critical for your Secure API Gateway project, where uncaught bottlenecks could cause outages during traffic spikes. Mastery here enables reliable systems that scale under real-world stress.