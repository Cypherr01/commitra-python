# Phase Introduction – Phase 0  
**Digital Museum – “Curating Artifacts of Knowledge”**

---

## 1. Project Context  

| Item | Details |
|------|---------|
| **Project** | **Digital Museum** – a web‑based platform where users can create virtual exhibits of artifacts, each with a description and a link to an online resource. |
| **Tagline** | *Curating Artifacts of Knowledge* |
| **Description** | The system will let educational institutions and researchers showcase collections online. Users add artifacts, write descriptions, attach URLs, and browse exhibits through a clean web UI. |
| **Technology Stack** | • **Python** – core language <br>• **Flask** – lightweight web framework <br>• **SQLite** – file‑based relational database (easy for beginners) |
| **Target Audience** | Beginners who are learning Python through a concrete, project‑anchored roadmap. |

---

## 2. Phase 0 Purpose  

Phase 0 builds the **foundational computing knowledge** required to run, develop, and understand the Digital Museum project.  
Learners will:

* Gain a mental model of how computers store and process information.  
* Set up a personal development environment that can host the project.  
* Acquire the command‑line, file‑system, and networking basics that underpin any web application.  
* Begin thinking like a programmer—breaking a real‑world problem (curating artifacts) into logical steps.

---

## 3. Learning Objectives  

By the end of Phase 0 you will be able to:

1. **Explain** what a computer is and how its hardware/software layers interact.  
2. **Convert** numbers between decimal, binary, octal, and hexadecimal – the basis for data storage.  
3. **Describe** bits, bytes, and common data representations (integers, strings, images).  
4. **Identify** core operating‑system concepts (processes, memory, file I/O).  
5. **Navigate** a file system, create directories, and manage files for project assets.  
6. **Use** a terminal/command‑line to run commands, edit files, and invoke Python scripts.  
7. **Outline** how the Internet transports data (IP, DNS, HTTP) and why a web server is needed.  
8. **Set up** a development environment: code editor, Python interpreter, virtual environment, Git version control.  
9. **Write** simple Python statements that model “curating an artifact” (data structures, functions).  
10. **Reflect** on challenges, document learning, and adopt a growth‑mindset approach.

---

## 4. Topic‑to‑Project Connection Map  

| Topic (Phase 0) | Direct Project Connection |
|-----------------|---------------------------|
| **0.1 What is a Computer?** | Set up a basic computer system to run the project. |
| **0.2 Binary & Number Systems** | Implement binary and number‑system calculations to store artifact metadata (e.g., IDs, timestamps). |
| **0.3 Bits, Bytes & Data Representation** | Represent artifact data using bits, bytes, and appropriate Python data structures (dicts, classes). |
| **0.4 Operating System Basics** | Understand the OS layer that will host Flask and SQLite. |
| **0.5 File Systems & Directories** | Create a folder hierarchy for source code, static assets, and the SQLite database. |
| **0.6 Command Line & Terminal** | Build a CLI tool for quick artifact entry and project management. |
| **0.7 How the Internet Works** | Design the network layout (local dev server → browser) and grasp HTTP request/response cycles. |
| **0.8 Dev Environment Setup** | Install VS Code (or another editor), Python, create a virtualenv, and initialise a Git repo. |
| **0.9 What is Programming?** | Write the core logic that adds, edits, and displays artifacts in the museum. |
| **0.10 Growth Mindset for Engineering** | Reflect on progress, document bugs, and iterate on the museum prototype. |

---

## 5. Suggested Learning Path (Sequential)

1. **0.1 – What is a Computer?** – Watch a short video, then write a one‑paragraph description of the layers (hardware → OS → application).  
2. **0.2 – Binary & Number Systems** – Practice converting IDs (e.g., 1010₂ → 10₁₀) with an online converter or a tiny Python script.  
3. **0.3 – Bits, Bytes & Data Representation** – Explore how strings become bytes (`'art'.encode('utf‑8')`).  
4. **0.4 – Operating System Basics** – Install a lightweight Linux VM or use WSL/macOS Terminal; list running processes.  
5. **0.5 – File Systems & Directories** – Create the project folder structure: `museum/`, `museum/static/`, `museum/templates/`, `museum/db/`.  
6. **0.6 – Command Line & Terminal** – Learn `cd`, `ls`, `mkdir`, `python -m venv venv`, `source venv/bin/activate`.  
7. **0.7 – How the Internet Works** – Draw a diagram: Browser ↔ HTTP ↔ Flask server ↔ SQLite DB.  
8. **0.8 – Dev Environment Setup** – Install VS Code, the Python extension, Git; initialise a repo and make the first commit.  
9. **0.9 – What is Programming?** – Write a simple `Artifact` class with `title`, `description`, `url`; instantiate a few objects.  
10. **0.10 – Growth Mindset** – Keep a learning journal; after each topic, note “What went well?” and “What will I improve?”.  

---

## 6. Mini‑Activities & Deliverables  

| Activity | Goal | Expected Output |
|----------|------|-----------------|
| **A. System Checklist** | Verify OS, Python version, Git installed. | Screenshot of `python --version` and `git --version`. |
| **B. Binary Calculator** | Write a CLI script `bincalc.py` that converts between bases. | `bincalc.py 42 --to binary` → `101010`. |
| **C. File‑Structure Setup** | Create the project directory tree and add a placeholder `README.md`. | Directory listing (`tree museum`). |
| **D. Git Init & First Commit** | Initialise repo, add files, commit with a meaningful message. | Git log showing the first commit. |
| **E. Artifact Class Prototype** | Define a Python class and instantiate three sample artifacts. | `artifact.py` with class definition and a `print` of objects. |
| **F. Reflection Log** | Write a 200‑word reflection on the biggest challenge faced. | `reflection.txt`. |

All deliverables are stored in the `museum/` folder and committed to the repository.

---

## 7. Resources & References  

| Type | Link / Title |
|------|--------------|
| **Intro Video** | “How Computers Work – 5‑Minute Overview” (YouTube) |
| **Binary Converter** | <https://www.rapidtables.com/convert/number/binary-to-decimal.html> |
| **Python Docs – Data Types** | <https://docs.python.org/3/tutorial/introduction.html#data-types> |
| **Flask Quick‑Start** | <https://flask.palletsprojects.com/en/3.0.x/quickstart/> |
| **Git Basics** | <https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control> |
| **Growth Mindset Article** | Dweck, C. *Mindset: The New Psychology of Success* (summary) |
| **Terminal Cheat Sheet** | <https://www.makeuseof.com/tag/linux-terminal-commands-cheat-sheet/> |

---

## 8. Success Criteria for Phase 0  

- **Environment** – Python 3.11+, Flask, SQLite installed; virtual environment active.  
- **Version Control** – Git repository with at least three commits (setup, binary script, artifact class).  
- **File System** – Project folder hierarchy matches the template.  
- **CLI Tools** – `bincalc.py` works for decimal ↔ binary ↔ hex conversions.  
- **Artifact Prototype** – A functional `Artifact` class that can be instantiated and printed.  
- **Reflection** – A concise journal entry demonstrating awareness of learning process.  

When all criteria are met, you are ready to move on to **Phase 1 – Building the Flask Backend**.

--- 

*Happy curating! 🎨🚀*