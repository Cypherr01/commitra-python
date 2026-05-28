# Phase 0 – Foundations & Project Overview  
**Project:** Digital Museum | **Tagline:** *Curating Artifacts of Knowledge*  
**Stack:** Python, Flask, SQLite  

---

## 1. Phase Purpose  
Phase 0 establishes the essential computing concepts, tooling, and mindset needed to build the Digital Museum. It equips learners with a solid foundation before they start writing Python code for the web‑based exhibit.

---

## 2. Learning Objectives  

| Objective | How it ties to the Digital Museum |
|-----------|-----------------------------------|
| **Understand what a computer is** | Be able to set up a workstation that can run the museum application. |
| **Master binary & other number systems** | Perform low‑level calculations for artifact IDs, timestamps, and metadata storage. |
| **Grasp bits, bytes & data representation** | Choose appropriate data structures (e.g., integers, strings, blobs) for artifact information. |
| **Learn OS fundamentals** | Configure the operating system (Windows/macOS/Linux) to host Flask and SQLite. |
| **Navigate file systems & directories** | Organize project files, static assets, and a persistent SQLite database. |
| **Use the command line/terminal** | Run development servers, manage virtual environments, and execute scripts. |
| **Comprehend how the Internet works** | Design a simple network layout (local dev server → browser) and plan future deployment. |
| **Set up a development environment** | Install a code editor, Git, and create a reproducible Python environment. |
| **Introduce programming concepts** | Write the first Python functions that curate artifacts and generate exhibit pages. |
| **Cultivate a growth mindset** | Reflect on challenges, iterate on solutions, and adopt continuous‑learning habits. |

---

## 3. Topic‑to‑Project Connection Map  

| Phase 0 Sub‑topic | Project‑level Activity |
|-------------------|------------------------|
| **0.1 What is a Computer?** | Install and configure a laptop/desktop that can run Python, Flask, and SQLite. |
| **0.2 Binary & Number Systems** | Implement simple scripts that convert artifact IDs to binary/hex for storage checks. |
| **0.3 Bits, Bytes & Data Representation** | Model an artifact record (title, description, URL) using appropriate Python data types. |
| **0.4 Operating System Basics** | Choose and configure a OS (e.g., Ubuntu) to host the development server. |
| **0.5 File Systems & Directories** | Create the project folder layout: `app/`, `static/`, `templates/`, `data/`. |
| **0.6 Command Line & Terminal** | Use `git`, `python -m venv`, `flask run` to manage the codebase and launch the app. |
| **0.7 How the Internet Works** | Sketch a network diagram showing the local host, browser, and eventual cloud host. |
| **0.8 Dev Environment Setup** | Install VS Code (or PyCharm), Git, and set up a GitHub repository for version control. |
| **0.9 What is Programming?** | Write a “curate_artifact()” function that validates input and stores it in SQLite. |
| **0.10 Growth Mindset for Engineering** | Keep a learning journal; conduct weekly retrospectives on what worked and what didn’t. |

---

## 4. Deliverables  

1. **Working Development Machine** – OS installed, Python 3.x, Flask, SQLite, Git, and a code editor ready.  
2. **Project Repository** – Initialized Git repo with a clear README, `.gitignore`, and basic folder structure.  
3. **Command‑Line Cheat Sheet** – Common commands for virtual environments, Flask server, and Git operations.  
4. **Artifact Metadata Script** – A small Python script that demonstrates binary/decimal conversion and writes a sample record to a SQLite DB.  
5. **Reflection Log** – One‑page summary of challenges faced, solutions tried, and lessons learned.

---

## 5. Suggested Timeline (2 weeks)

| Day | Activity |
|-----|----------|
| 1‑2 | Set up hardware, install OS updates, install Python & Git. |
| 3‑4 | Learn binary/number systems; complete the conversion script. |
| 5‑6 | Explore bits/bytes; design the artifact data model. |
| 7   | Install Flask & SQLite; create the project folder layout. |
| 8‑9 | Practice terminal commands; run a “Hello Flask” app. |
|10   | Draft the network diagram and discuss future deployment options. |
|11‑12| Configure VS Code (or preferred IDE); commit initial repo. |
|13   | Write the first `curate_artifact()` function and store a record. |
|14   | Write a brief reflection; prepare for Phase 1 (Python fundamentals). |

---

## 6. Resources  

| Type | Title / Link |
|------|--------------|
| **Reading** | *Computer Science 101* – Chapter 1 “What Is a Computer?” |
| **Video** | CrashCourse – “Binary Numbers” (YouTube) |
| **Tutorial** | Real Python – “Flask Quickstart” |
| **Tool Docs** | Python.org – *Installing Python*; SQLite.org – *Getting Started* |
| **Mindset** | Carol Dweck – *Mindset: The New Psychology of Success* (selected chapters) |

---

## 7. Assessment Checklist  

- [ ] Can the learner boot the machine and launch a Flask development server?  
- [ ] Does the learner understand how binary maps to decimal and can perform conversions in Python?  
- [ ] Is the project directory correctly organized and version‑controlled?  
- [ ] Has the learner created a SQLite database and inserted a test artifact record?  
- [ ] Has the learner documented at least three challenges and the steps taken to overcome them?  

---

### Closing Note  

Phase 0 is the launchpad for the Digital Museum. By mastering these foundational concepts and setting up a reliable development environment, learners will be ready to dive into core Python programming, web development with Flask, and data persistence with SQLite in the subsequent phases. Embrace curiosity, experiment boldly, and remember that every obstacle is an opportunity to grow. Happy building!