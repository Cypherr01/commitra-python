## What Is This?
Dev Environment Setup refers to the process of configuring a development environment to write, test, and manage code efficiently. A good analogy for this concept is setting up a workshop for a carpenter. Just as a carpenter needs a well-organized workspace with the right tools to build furniture, a developer needs a well-configured development environment with the right tools to build software.

## How It Works Internally
### Installing Python 3.x Correctly
To start setting up a development environment, we need to install Python 3.x correctly. This involves downloading the latest version of Python from the official website and following the installation instructions for our operating system.

### VS Code — Installation, Extensions
Next, we need to install a code editor like VS Code, which provides a user-friendly interface for writing and editing code. We also need to install extensions like Pylance, Python, and GitLens to enhance the functionality of our code editor.

### Virtual Environments — Why One Per Project
A virtual environment is a self-contained Python environment that allows us to isolate our project's dependencies from the system Python environment. We should use one virtual environment per project to avoid conflicts between different projects.

### `pip` — Installing and Managing Packages
`pip` is the package installer for Python, which allows us to easily install and manage packages for our project. We can use `pip` to install packages from the Python Package Index (PyPI) or from other sources.

### `.env` Files — Storing Secrets Outside Code
`.env` files are used to store sensitive information like API keys or database credentials outside of our code. This helps to keep our code secure and avoid exposing sensitive information to others.

### Git — Installation and Global Config
Git is a version control system that helps us to track changes to our code over time. We need to install Git and configure it globally on our system to use it with our code editor.

### GitHub — Creating an Account and First Repository
GitHub is a web-based platform for version control and collaboration. We need to create a GitHub account and set up our first repository to store and manage our code.

### `.gitignore` — What to Never Commit
The `.gitignore` file is used to specify files or directories that should be ignored by Git. We should never commit files like `venv`, `.env`, or `__pycache__` to our repository, as they contain sensitive information or are generated automatically.

### SSH Keys for GitHub
SSH keys are used to securely connect to our GitHub repository from our local machine. We need to generate an SSH key pair and add the public key to our GitHub account to enable secure connections.

## Syntax and Structure
```text
# STEP 1: Install Python 3.x from the official website
# STEP 2: Install VS Code and extensions like Pylance, Python, and GitLens
# STEP 3: Create a new virtual environment for our project
# STEP 4: Activate the virtual environment and install packages using pip
# STEP 5: Create a .env file to store sensitive information
# STEP 6: Install Git and configure it globally on our system
# In Phase 1 we will write this in real code.
```

## Practical Example
This section is omitted for Phase 0, as no runnable code exists yet.

## How This Connects to the Project
Before setting up a development environment, our Digital Museum project would not have a clear structure or organization. After setting up the environment, we can start writing and managing our code efficiently. The exact file and function name where this concept lives in the project is not applicable yet, as we have not started writing code. A real company that uses this exact pattern is GitHub, which provides a platform for developers to manage their code and collaborate with others.

## Common Mistakes Beginners Make
**Wrong idea:** Installing only the basic Python interpreter without any additional tools or extensions.
**Correct idea:** Installing a code editor like VS Code and extensions like Pylance, Python, and GitLens to enhance functionality.
Wrong idea: Not using virtual environments and installing packages globally.
Correct idea: Using one virtual environment per project to avoid conflicts.
Wrong idea: Hardcoding sensitive information directly into our code.
Correct idea: Storing sensitive information in .env files and ignoring them in our Git repository.
Wrong idea: Not configuring Git correctly and trying to use it without a GitHub account.
Correct idea: Configuring Git globally and creating a GitHub account to manage our code and collaborate with others.

## Verification Task 1
Debug This: Our system shows an error message when trying to install a package using pip. We have evidence that the package is available on PyPI. Diagnose and fix the issue.

## Solution 1
The issue might be due to a conflict with an existing package or a missing dependency. We need to check the package's documentation and dependencies to resolve the issue.

## Verification Task 2
Design Decision: We are building a new feature for our Digital Museum project and need to decide whether to use a relational database or a NoSQL database. Defend using this topic.

## Solution 2
We should use a relational database for our Digital Museum project because it provides a structured and organized way to store and manage data. This topic has taught us about the importance of setting up a development environment and using tools like Git and GitHub to manage our code.

## Verification Task 3
Code Review: Our team member has written a script to automate the deployment of our Digital Museum project. However, the script is not using a virtual environment and is installing packages globally. Find and fix the bug.

## Solution 3
The bug in the script is that it is not using a virtual environment and is installing packages globally. This can cause conflicts with other projects and make it difficult to manage dependencies. We should modify the script to use a virtual environment and install packages locally.

## What Comes Next
The next topic in our roadmap is Growth Mindset for Engineering. This topic follows logically from Dev Environment Setup because having a well-configured development environment is essential for writing and managing code efficiently, and a growth mindset is necessary for continuous learning and improvement in software development. The concept of virtual environments from this topic will reappear in Growth Mindset for Engineering as we discuss how to approach challenges and learn from failures in software development.

## Reference Summary
Dev Environment Setup is the process of configuring a development environment to write, test, and manage code efficiently. It involves installing Python 3.x, setting up a code editor like VS Code, using virtual environments, and managing packages with pip. We also need to store sensitive information in .env files and ignore them in our Git repository. A common mistake beginners make is not using virtual environments and installing packages globally. This concept is essential for our Digital Museum project, as it provides a clear structure and organization for our code. By setting up a development environment correctly, we can write and manage our code efficiently and collaborate with others using Git and GitHub. This concept enables us to move on to the next topic, Growth Mindset for Engineering, where we will learn how to approach challenges and learn from failures in software development.