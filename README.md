# EECE 6399 – Project 0: Environment Setup, Python, Git, and Autograder Tutorial

**Course:** EECE 6399 – AI for Autonomous Systems  
**University:** The University of Texas Rio Grande Valley (UTRGV)  
**Term:** Fall 2026  
**Instructor:** Dr. Lei Cheng  

> **Points: 0 – Practice / onboarding project**
>
> Project 0 does **not** count toward the final course grade.
>
> However, you are strongly encouraged to complete the entire setup and tutorial before starting Project 1.

---

# Project Overview

Project 0 prepares your computer and development workflow for the programming projects in EECE 6399.

The Project 0 repository already contains a small Python programming tutorial and autograder. You do **not** need to download a separate tutorial package.

By the end of Project 0, you should be able to:

- install and use Miniconda;
- create a dedicated Python 3.12 environment for EECE 6399;
- install NumPy, Matplotlib, PyTorch, and TorchVision;
- verify that Tkinter and project graphics can run;
- use Visual Studio Code with the correct Python interpreter;
- navigate a project folder from the terminal;
- recognize where your code belongs in the starter files;
- run the local autograder;
- run one question at a time;
- interpret `PASS`, `FAIL`, tracebacks, and `Provisional grades`;
- complete the included three-question tutorial;
- use Git to save and push your work;
- understand the difference between local testing and official course grading.

The recommended Conda environment name for this course is:

```text
eece6399
```

Use this same environment for Projects 1–5.

---

# 1. Project 0 Repository

Your Project 0 repository is already organized as a course starter repository.

It should contain files similar to:

```text
project0-setup-template/
│
├── README.md
├── addition.py
├── autograder.py
├── buyLotsOfFruit.py
├── grading.py
├── projectParams.py
├── shop.py
├── shopSmart.py
├── testClasses.py
├── testParser.py
├── tutorialTestClasses.py
├── test_cases/
├── .gitignore
└── .gitattributes
```

The three main practice files you will edit are:

```text
addition.py
buyLotsOfFruit.py
shopSmart.py
```

The other files support the tutorial, testing, and autograder.

Do not modify grading infrastructure simply to make a test appear to pass.

---

# 2. Required Software

You will need:

1. **Miniconda** or another working Conda installation
2. **Python 3.12**
3. **Git**
4. A code editor such as **Visual Studio Code**
5. Python packages:
   - NumPy
   - Matplotlib
   - PyTorch
   - TorchVision
6. Tkinter for graphical projects

A dedicated NVIDIA GPU is **not required**.

All required course assignments can be completed using CPU execution.

---

# 3. Install Miniconda

Miniconda is recommended because it allows you to create an isolated Python environment for EECE 6399.

Official Miniconda page:

https://docs.conda.io/projects/miniconda/en/latest/

If you already have Anaconda or Miniconda installed and `conda` works correctly, you do not need to install another copy.

---

## 3.1 Windows

1. Download the Windows Miniconda installer.
2. Run the `.exe` installer.
3. Choose **Just Me** unless you specifically need a system-wide installation.
4. The default installation location is usually fine.
5. Complete the installer.

After installation, open:

```text
Anaconda Prompt (Miniconda3)
```

Test Conda:

```bash
conda --version
```

You should see a version number.

### PowerShell setup

If you want to use Conda in Windows PowerShell, run once from the Miniconda/Anaconda prompt:

```powershell
conda init powershell
```

Then close all PowerShell windows and open a new one.

Test:

```powershell
conda --version
```

---

## 3.2 macOS

Download the Miniconda installer appropriate for your Mac:

- Apple Silicon / ARM64 for most newer Macs
- Intel / x86_64 for older Intel Macs

Install Miniconda using the official package or shell installer.

Open Terminal and run:

```bash
conda --version
```

If Conda is not available, initialize the default macOS shell:

```bash
conda init zsh
```

Close Terminal, reopen it, and test again.

---

## 3.3 Linux

For a typical x86-64 Linux system, install Miniconda using the appropriate shell installer.

For example:

```bash
bash Miniconda3-latest-Linux-x86_64.sh
```

Follow the prompts.

If necessary:

```bash
conda init bash
```

Then close and reopen the terminal.

Verify:

```bash
conda --version
```

---

# 4. Create the EECE 6399 Environment

Create a dedicated environment:

```bash
conda create --name eece6399 python=3.12
```

When prompted:

```text
Proceed ([y]/n)?
```

enter:

```text
y
```

Activate the environment:

```bash
conda activate eece6399
```

Your prompt should now begin with something similar to:

```text
(eece6399)
```

For example:

```text
(eece6399) PS C:\Users\Student\Documents\EECE6399>
```

or:

```text
(eece6399) student@computer:~/EECE6399$
```

---

# 5. Verify Python 3.12

With the environment active:

```bash
python --version
```

You should see:

```text
Python 3.12.x
```

The final patch number does not have to match exactly.

You can also run:

```bash
python -c "import sys; print(sys.executable); print(sys.version)"
```

This shows:

- the Python executable currently being used;
- the full Python version.

---

# 6. Make Sure You Are Using the Correct Python

Many students have multiple Python installations on the same computer.

Always activate the course environment first:

```bash
conda activate eece6399
```

Then check which Python is active.

### Windows PowerShell

```powershell
Get-Command python
```

or:

```powershell
where.exe python
```

### macOS / Linux

```bash
which python
```

The path should point to the `eece6399` Conda environment.

If it points to an unrelated system Python installation, stop and fix the environment before continuing.

---

# 7. Upgrade pip

With `eece6399` active:

```bash
python -m pip install --upgrade pip
```

For this course, we recommend:

```text
python -m pip
```

instead of only:

```text
pip
```

because it makes it clearer which Python installation receives the package.

---

# 8. Install NumPy and Matplotlib

Install:

```bash
python -m pip install numpy==1.26.4 matplotlib
```

Verify NumPy:

```bash
python -c "import numpy; print('NumPy:', numpy.__version__)"
```

Verify Matplotlib:

```bash
python -c "import matplotlib; print('Matplotlib:', matplotlib.__version__)"
```

You should not see an import error.

---

# 9. Install PyTorch and TorchVision

PyTorch is required for the machine-learning project later in the course.

Install it now so that environment problems are discovered early:

```bash
python -m pip install torch torchvision
```

Verify PyTorch:

```bash
python -c "import torch; print('PyTorch:', torch.__version__)"
```

Test tensor creation:

```bash
python -c "import torch; print(torch.rand(3, 3))"
```

You should see a 3×3 tensor containing random numbers.

Verify TorchVision:

```bash
python -c "import torchvision; print('TorchVision:', torchvision.__version__)"
```

---

## 9.1 GPU / CUDA Check

Run:

```bash
python -c "import torch; print('CUDA available:', torch.cuda.is_available())"
```

If you see:

```text
CUDA available: False
```

that is completely acceptable.

A GPU is **not required** for EECE 6399.

---

## 9.2 Optional NVIDIA GPU Support

If you specifically want to use an NVIDIA GPU, use the official PyTorch installation selector:

https://pytorch.org/get-started/locally/

Select:

```text
Operating System
Package: Pip
Language: Python
Compute Platform: appropriate CUDA version
```

Then use the command generated by the official site.

Do not install random CUDA packages from unrelated tutorials.

GPU support is optional.

---

# 10. Verify Tkinter and Graphics

Projects 1–4 may open graphical windows.

Test Tkinter:

```bash
python -m tkinter
```

A small window should appear.

Close it after confirming that it works.

You can also test:

```bash
python -c "import tkinter; print('Tkinter OK')"
```

If Tkinter is missing in the Conda environment:

```bash
conda install tk
```

Then test again.

Most autograders can also be run without graphics:

```bash
python autograder.py --no-graphics
```

---

# 11. Final Environment Verification

With:

```bash
conda activate eece6399
```

run:

```bash
python --version
```

```bash
python -c "import numpy; print('NumPy OK:', numpy.__version__)"
```

```bash
python -c "import matplotlib; print('Matplotlib OK:', matplotlib.__version__)"
```

```bash
python -c "import torch; print('PyTorch OK:', torch.__version__)"
```

```bash
python -c "import torchvision; print('TorchVision OK:', torchvision.__version__)"
```

```bash
python -c "import tkinter; print('Tkinter OK')"
```

A successful setup should produce no import errors.

---

## 11.1 Optional One-Command Verification

You may also run:

```bash
python -c "import sys, numpy, matplotlib, torch, torchvision, tkinter; print('Python:', sys.version.split()[0]); print('NumPy:', numpy.__version__); print('Matplotlib:', matplotlib.__version__); print('PyTorch:', torch.__version__); print('TorchVision:', torchvision.__version__); print('CUDA:', torch.cuda.is_available()); print('Tkinter: OK')"
```

---

# 12. Activate the Environment Every Time

Whenever you open a new terminal to work on EECE 6399:

```bash
conda activate eece6399
```

Then move into your project repository:

```bash
cd path/to/project
```

Example:

```bash
cd path/to/project0-setup-template
```

Then you can run:

```bash
python autograder.py
```

When finished:

```bash
conda deactivate
```

---

# 13. Visual Studio Code Setup

Visual Studio Code is recommended but not required.

Official download page:

https://code.visualstudio.com/

Install the official **Python** extension from Microsoft.

---

## 13.1 Select the Correct Python Interpreter

Open your project repository in VS Code.

Then:

1. Press `Ctrl+Shift+P` on Windows/Linux or `Cmd+Shift+P` on macOS.
2. Search for:

```text
Python: Select Interpreter
```

3. Choose the interpreter associated with:

```text
eece6399
```

If VS Code uses the wrong interpreter, it may incorrectly report that packages such as PyTorch are missing.

---

## 13.2 Open a Terminal in VS Code

Use:

```text
Terminal → New Terminal
```

Check whether the terminal prompt begins with:

```text
(eece6399)
```

If not:

```bash
conda activate eece6399
```

Then verify:

```bash
python --version
```

---

# 14. Basic Terminal Commands

You do not need to become a terminal expert, but you should know the following commands.

## Current directory

### Windows PowerShell

```powershell
Get-Location
```

### macOS / Linux

```bash
pwd
```

---

## List files

### Windows PowerShell

```powershell
Get-ChildItem
```

or:

```powershell
ls
```

### macOS / Linux

```bash
ls
```

---

## Change directory

```bash
cd folder_name
```

Move up one directory:

```bash
cd ..
```

---

# 15. Where to Write Your Code

Throughout the programming projects, you will see markers like:

```python
"*** YOUR CODE HERE ***"
```

Whenever you see this marker:

> **Write your implementation below it, starting on a new line.**

---

## 15.1 Correct Example

Starter code:

```python
def example_function(x):
    "*** YOUR CODE HERE ***"
    return None
```

Your implementation should look like:

```python
def example_function(x):
    "*** YOUR CODE HERE ***"
    result = x * 2
    return result
```

Your code begins on the line **below** the marker.

---

## 15.2 Incorrect Example

Do not write:

```python
def example_function(x):
    "*** YOUR CODE HERE ***" result = x * 2
    return result
```

This is invalid Python.

---

## 15.3 Placeholder Code

You may see placeholder code such as:

```python
"*** YOUR CODE HERE ***"
util.raiseNotDefined()
```

or:

```python
"*** YOUR CODE HERE ***"
return None
```

or:

```python
"*** YOUR CODE HERE ***"
pass
```

Once you implement the function, replace or remove the placeholder behavior as needed.

Do not leave `util.raiseNotDefined()` in a function you believe is complete.

---

# 16. Do Not Rename Required Interfaces

The autograder expects specific:

- filenames;
- class names;
- function names;
- method names;
- arguments;
- return types.

If the starter provides:

```python
def add(a, b):
```

do not rename it to:

```python
def my_addition_function(a, b):
```

Even if your new function is correct, the autograder may not know how to call it.

---

# 17. Project 0 Practice Tutorial

Project 0 includes a short three-question Python tutorial directly in the repository.

It is designed to teach the same development workflow you will use later:

```text
read the assignment
        ↓
open starter code
        ↓
find "*** YOUR CODE HERE ***"
        ↓
write code below the marker
        ↓
save
        ↓
run autograder
        ↓
read PASS / FAIL
        ↓
debug
        ↓
rerun
```

> **Points: 0 – Practice only**
>
> The tutorial does **not** count toward your final EECE 6399 grade.
>
> You are strongly encouraged to reach **3/3** before starting Project 1.

---

# 18. First Run of the Tutorial

From the Project 0 repository root:

```bash
conda activate eece6399
```

Then:

```bash
python autograder.py
```

The untouched starter code is intentionally incomplete.

You may initially see:

```text
Provisional grades
==================
Question q1: 0/1
Question q2: 0/1
Question q3: 0/1
------------------
Total: 0/3
```

This is normal.

A zero on untouched starter code does **not** mean your environment is broken.

---

# 19. Practice Question 1 – Addition

Open:

```text
addition.py
```

Find the required addition function.

Your task is to return the sum of its two inputs.

Remember:

```python
"*** YOUR CODE HERE ***"
```

Write your implementation on the next line.

Test only Question 1:

```bash
python autograder.py -q q1
```

When correct, you should see:

```text
### Question q1: 1/1 ###
```

The main purpose is to practice:

```text
edit
→ save
→ test
→ inspect result
```

---

# 20. Practice Question 2 – Buying Fruit

Open:

```text
buyLotsOfFruit.py
```

You will work with an order represented by pairs such as:

```python
[
    ("apples", 2.0),
    ("pears", 3.0),
    ("limes", 4.0),
]
```

The starter file provides fruit prices.

Your task is to compute the total cost of the order according to the starter-code contract.

Again, write your implementation below:

```python
"*** YOUR CODE HERE ***"
```

Test:

```bash
python autograder.py -q q2
```

Read any failing messages carefully.

---

# 21. Practice Question 3 – Choosing the Best Shop

Open:

```text
shopSmart.py
```

You are given:

- an order;
- multiple fruit shops;
- different prices at different shops.

Your function should determine which shop offers the lowest total cost for the complete order.

The supporting file:

```text
shop.py
```

contains functionality used by this exercise.

You normally do not need to modify it.

Test:

```bash
python autograder.py -q q3
```

This exercise introduces an important idea:

> Use existing classes and helper functions rather than rewriting everything yourself.

---

# 22. Run the Complete Practice Autograder

After Q1, Q2, and Q3 pass individually:

```bash
python autograder.py
```

Your final practice result should be:

```text
Provisional grades
==================
Question q1: 1/1
Question q2: 1/1
Question q3: 1/1
------------------
Total: 3/3
```

For EECE 6399:

```text
3/3 = Project 0 tutorial successfully completed
```

but:

```text
3/3 does NOT add points to your final course grade
```

---

# 23. Running One Question at a Time

During development, do not run the entire project after every small edit.

Use:

```bash
python autograder.py -q q1
```

or:

```bash
python autograder.py -q q2
```

or:

```bash
python autograder.py -q q3
```

Recommended workflow:

```text
implement Q1
   ↓
test Q1
   ↓
fix Q1
   ↓
move to Q2
   ↓
test Q2
   ↓
move to Q3
   ↓
run full autograder
```

This same workflow applies to Projects 1–5.

---

# 24. Understanding `PASS` and `FAIL`

A passing test may show:

```text
*** PASS
```

or:

```text
*** PASS: test_cases/...
```

A failing test may show:

```text
*** FAIL
```

or:

```text
*** FAIL: test_cases/...
```

The lines around the failure may include:

- expected output;
- student output;
- an exception;
- a traceback;
- the name of the failed test.

Read the traceback from the bottom upward to identify the immediate error.

---

# 25. Understanding `Provisional grades`

At the end of an autograder run, you may see:

```text
Provisional grades
==================
...
```

`Provisional` means:

> This is the result of the local autograder run.

Running the local autograder does **not** automatically submit your assignment.

Your GitHub repository must still contain your latest work.

For graded projects, follow the official EECE 6399 submission workflow.

---

# 26. Debugging with `print`

You may temporarily add debugging output:

```python
print("Current value:", value)
```

Then rerun the relevant question.

For example:

```bash
python autograder.py -q q2
```

This can help answer:

```text
What input did my function receive?
What value did I calculate?
Which branch of my code executed?
```

Remove unnecessary debugging output before final submission.

---

# 27. Local Autograder vs. Official Course Grading

Projects include local testing infrastructure so you can debug your work before submission.

The local repository may contain:

```text
autograder.py
grading.py
test_cases/
testClasses.py
```

These files are useful for development.

However, official grading is performed using instructor-controlled grading infrastructure.

The basic workflow is:

```text
Student edits required source files
        ↓
Student runs local autograder
        ↓
Student commits changes
        ↓
Student pushes to GitHub
        ↓
Course submission is evaluated
        ↓
Instructor-controlled clean grading environment is used
        ↓
Official score is produced
```

---

# 28. Why Official Grading Uses a Clean Environment

Official grading should evaluate your implementation, not student-modified grading infrastructure.

Therefore, changing files such as:

```text
autograder.py
grading.py
test_cases/
```

does not constitute a valid solution.

For the graded programming projects, the course grader evaluates the required student-editable source files inside a clean grading environment.

This helps ensure that everyone is evaluated consistently.

---

# 29. Local Score vs. Course Score

Some programming projects use an internal technical point scale.

For example, a local autograder may show:

```text
25/25
```

while the EECE 6399 course assignment is recorded as:

```text
100/100
```

The course grading system performs the appropriate conversion.

Do not modify the autograder in an attempt to change the displayed scale.

Project 0 itself remains:

```text
0 course points
```

regardless of whether the practice tutorial reports `3/3`.

---

# 30. Git Setup

Check Git:

```bash
git --version
```

If Git is missing, install it from:

https://git-scm.com/

---

## 30.1 Configure Git Identity

If this is your first time using Git:

```bash
git config --global user.name "Your Name"
```

```bash
git config --global user.email "your-email@example.com"
```

Use an email associated with your GitHub account when possible.

---

# 31. Basic Git Workflow

Inside your project repository:

```bash
git status
```

This shows changed files.

Stage a file:

```bash
git add filename.py
```

For Project 0, for example:

```bash
git add addition.py buyLotsOfFruit.py shopSmart.py
```

Commit:

```bash
git commit -m "Complete Project 0 tutorial"
```

Push:

```bash
git push
```

---

# 32. Commit Frequently

Do not wait until the deadline to make your first commit.

A good workflow for graded projects is:

```text
complete one question
        ↓
test it
        ↓
git add
        ↓
git commit
        ↓
git push
```

Git gives you a history of working versions and reduces the chance of losing work.

---

# 33. Do Not Commit Generated Files

Generated files usually should not be committed.

Examples:

```text
__pycache__/
*.pyc
*.pyo
result.json
```

The course repository includes `.gitignore` rules for common generated files.

---

# 34. Recommended Workflow for Projects 1–5

Use this routine:

```text
Open terminal
        ↓
conda activate eece6399
        ↓
cd into project repository
        ↓
git pull
        ↓
read README.md
        ↓
open required source file
        ↓
find "*** YOUR CODE HERE ***"
        ↓
write code BELOW the marker
        ↓
run one question
        ↓
debug
        ↓
run full autograder
        ↓
git status
        ↓
git add
        ↓
git commit
        ↓
git push
        ↓
follow EECE 6399 submission instructions
```

---

# 35. PyTorch Concepts You Will Need Later

Project 0 is primarily environment setup, but because PyTorch is required later, it is useful to understand a few concepts now.

---

## 35.1 Tensors

PyTorch uses tensors as its main numerical data structure.

Example:

```python
import torch

x = torch.tensor([1.0, 2.0, 3.0])
print(x)
```

A tensor may represent:

```text
scalar
vector
matrix
higher-dimensional array
```

---

## 35.2 Linear Layers

A typical neural-network layer is:

```python
torch.nn.Linear(input_size, output_size)
```

Conceptually:

```text
y = xW + b
```

Trainable layers should normally be created in a model's `__init__` method and reused during forward computation.

---

## 35.3 ReLU

ReLU is a common non-linear activation:

```text
ReLU(x) = max(x, 0)
```

In PyTorch:

```python
torch.relu(x)
```

---

## 35.4 Loss Functions

For regression, a common loss is mean squared error.

For classification, cross entropy is commonly used.

Later projects will provide more detailed instructions.

---

## 35.5 Basic Training Loop

A typical PyTorch optimization step is:

```python
optimizer.zero_grad()
prediction = model(x)
loss = loss_function(prediction, y)
loss.backward()
optimizer.step()
```

You do not need to master this during Project 0, but your PyTorch installation should be ready.

---

# 36. Troubleshooting

## `conda` is not recognized

### Windows

Open:

```text
Anaconda Prompt (Miniconda3)
```

Then:

```powershell
conda init powershell
```

Close and reopen PowerShell.

### macOS

```bash
conda init zsh
```

### Linux

```bash
conda init bash
```

Then reopen the terminal.

---

## `conda activate eece6399` says the environment does not exist

Check:

```bash
conda env list
```

If `eece6399` is missing:

```bash
conda create --name eece6399 python=3.12
```

---

## Python is not version 3.12

Activate:

```bash
conda activate eece6399
```

Then:

```bash
python --version
```

Check the executable path if necessary.

Windows:

```powershell
where.exe python
```

macOS/Linux:

```bash
which python
```

---

## `ModuleNotFoundError: No module named 'torch'`

Activate the environment:

```bash
conda activate eece6399
```

Then:

```bash
python -m pip install torch torchvision
```

Verify:

```bash
python -c "import torch; print(torch.__version__)"
```

---

## `ModuleNotFoundError: No module named 'numpy'`

Run:

```bash
python -m pip install numpy==1.26.4
```

---

## `ModuleNotFoundError: No module named 'matplotlib'`

Run:

```bash
python -m pip install matplotlib
```

---

## Tkinter does not work

Try:

```bash
conda install tk
```

Then:

```bash
python -m tkinter
```

---

## PyTorch says CUDA is unavailable

That is acceptable.

CPU execution is sufficient for the course.

---

## VS Code cannot import packages

VS Code is probably using the wrong interpreter.

Choose:

```text
Python: Select Interpreter
```

and select:

```text
eece6399
```

---

## `pip` installs into the wrong environment

Use:

```bash
python -m pip install PACKAGE_NAME
```

rather than:

```bash
pip install PACKAGE_NAME
```

---

## Autograder says `Method not implemented`

A required starter function is probably still incomplete.

Find:

```python
"*** YOUR CODE HERE ***"
```

and write the implementation below it.

Also check whether:

```python
util.raiseNotDefined()
```

or another placeholder is still being executed.

---

## Autograder returns zero on untouched starter code

That is usually expected.

Starter code intentionally contains incomplete methods.

---

## Autograder produces a traceback

Read the final lines first.

Common causes include:

- syntax error;
- wrong function name;
- returning `None`;
- wrong number of arguments;
- unimplemented method;
- invalid type;
- incorrect indentation.

---

# 37. Environment Recovery

If the environment becomes badly misconfigured, recreating it may be easier than continuing to patch it.

Deactivate:

```bash
conda deactivate
```

Remove:

```bash
conda env remove --name eece6399
```

Create again:

```bash
conda create --name eece6399 python=3.12
```

Activate:

```bash
conda activate eece6399
```

Upgrade pip:

```bash
python -m pip install --upgrade pip
```

Install packages:

```bash
python -m pip install numpy==1.26.4 matplotlib
```

```bash
python -m pip install torch torchvision
```

If needed:

```bash
conda install tk
```

Then repeat the verification checks in this README.

---

# 38. Project 0 Completion Checklist

Before starting Project 1, verify every item below.

## Conda and Python

- [ ] Conda is installed.
- [ ] `conda --version` works.
- [ ] The `eece6399` environment exists.
- [ ] `conda activate eece6399` works.
- [ ] `python --version` reports Python 3.12.
- [ ] Python points to the `eece6399` environment.

## Packages

- [ ] NumPy imports successfully.
- [ ] Matplotlib imports successfully.
- [ ] PyTorch imports successfully.
- [ ] TorchVision imports successfully.
- [ ] A PyTorch tensor can be created.
- [ ] I understand that CUDA is optional.

## Graphics

- [ ] `import tkinter` works.
- [ ] `python -m tkinter` opens a test window on my graphical desktop.

## Development Tools

- [ ] Git is installed.
- [ ] `git --version` works.
- [ ] VS Code or another editor is installed.
- [ ] If using VS Code, the `eece6399` interpreter is selected.

## Code Editing

- [ ] I know to write code below `*** YOUR CODE HERE ***`.
- [ ] I know not to write code on the same line as the marker.
- [ ] I know not to rename required functions or classes.
- [ ] I understand that starter placeholders must be replaced when required.

## Tutorial

- [ ] I ran the untouched Project 0 autograder.
- [ ] I completed Question 1.
- [ ] I completed Question 2.
- [ ] I completed Question 3.
- [ ] I reached `3/3`.
- [ ] I understand that Project 0 carries 0 course points.

## Autograder

- [ ] I know how to run `python autograder.py`.
- [ ] I know how to run `python autograder.py -q q1`.
- [ ] I understand `PASS`.
- [ ] I understand `FAIL`.
- [ ] I understand `Provisional grades`.
- [ ] I understand that local grading does not automatically submit my work.

## Git and Submission

- [ ] I know how to use `git status`.
- [ ] I know how to use `git add`.
- [ ] I know how to use `git commit`.
- [ ] I know how to use `git push`.
- [ ] I understand that graded projects use the EECE 6399 GitHub workflow.
- [ ] I understand that official grading uses instructor-controlled grading infrastructure.

Once all items are complete, your environment and workflow are ready for **EECE 6399 Project 1**.

---

# 39. Recommended Development Habits

Throughout the semester:

- activate `eece6399` before working;
- read each project's README first;
- work on one question at a time;
- run focused tests frequently;
- read tracebacks rather than ignoring them;
- commit working versions;
- push regularly;
- do not wait until the deadline to test the full project;
- do not modify grading infrastructure as a substitute for solving the assignment.

A disciplined workflow will save substantial debugging time.

---

# 40. Project Framework Notice

This repository contains an educational Python programming and autograder framework adapted for:

**UTRGV EECE 6399 – AI for Autonomous Systems**

Course-facing setup instructions, grading workflow, submission procedures, and assignment guidance in this repository are specific to EECE 6399.

Please retain copyright and license notices already present in the distributed source files.

---

# Appendix A – Project 5: Machine Learning Reference

# EECE 6399 – Project 5: Machine Learning

**Course:** EECE 6399 – AI for Autonomous Systems  
**University:** The University of Texas Rio Grande Valley (UTRGV)  
**Term:** Fall 2026  
**Instructor:** Dr. Lei Cheng  

> **Due Date:** See UTRGV Brightspace for the official deadline.

---

## Project Overview

In this project, you will build and train several machine-learning models using PyTorch.

The project begins with the perceptron, one of the simplest trainable linear classifiers, and then moves to modern neural-network models for regression, image classification, sequence modeling, convolution, and attention.

You will implement and train models for:

- Binary classification with a perceptron
- Non-linear regression
- Handwritten digit classification
- Language identification with a recurrent model
- Convolutional neural networks
- Scaled dot-product attention
- An optional character-level GPT-style model

The required technical portion of Project 5 is worth **100 points total**.

Question 7, `character-GPT`, is worth **0 points**, but it is **optional and strongly encouraged** because it connects the attention mechanism from Question 6 to transformer-based generative language models.

---

## Learning Objectives

After completing this project, you should be able to:

- Explain the perceptron learning rule.
- Distinguish linear models from neural networks with non-linear activations.
- Build PyTorch models using trainable parameters and linear layers.
- Process data in mini-batches.
- Implement training loops using gradient-based optimization.
- Select appropriate loss functions for regression and classification.
- Understand the role of validation accuracy and stopping criteria.
- Design and tune small neural-network architectures.
- Explain why the final classification layer generally should not use ReLU.
- Build a recurrent architecture for variable-length sequences.
- Explain the purpose of convolution in image processing.
- Implement a basic two-dimensional convolution operation.
- Explain query, key, and value projections in attention.
- Implement scaled dot-product attention and a causal mask.
- Understand how attention is used inside transformer blocks.
- Connect character-level next-token prediction to modern language models.

---

# 1. Files You Will Edit

You are expected to modify the following required files:

```text
models.py
losses.py
train.py
```

For the optional Question 7, you will additionally work with:

```text
gpt_model.py
```

Do not rename provided functions, classes, methods, or required attributes.

---

# 2. Important Supporting Files

| File / Directory | Purpose |
|---|---|
| `autograder.py` | Local project autograder |
| `backend.py` | Dataset and task support code |
| `data/` | Datasets used by several project tasks |
| `models.py` | Required model definitions |
| `losses.py` | Required loss functions |
| `train.py` | Required training loops |
| `gpt_model.py` | Optional character-GPT model code |
| `chargpt.py` | Optional character-GPT training / generation driver |

You should normally leave supporting files unchanged unless a question explicitly tells you otherwise.

---

# 3. Environment Setup

Project 5 requires:

- Python
- NumPy
- Matplotlib
- PyTorch

Before starting, run:

```bash
python autograder.py --check-dependencies
```

You can also verify the installed package versions:

```bash
python -c "import torch; print(torch.__version__)"
python -c "import numpy; print(numpy.__version__)"
python -c "import matplotlib; print(matplotlib.__version__)"
```

If the dependency check succeeds, do not change package versions unnecessarily.

If you encounter a NumPy compatibility problem, a NumPy version below 2.0 may be more compatible with the provided starter framework.

---

# 4. Running the Autograder

Run the complete project:

```bash
python autograder.py --no-graphics
```

Run one question:

```bash
python autograder.py -q q3
```

Run one question without graphics:

```bash
python autograder.py -q q3 --no-graphics
```

The full project can take significantly longer than Projects 1–4 because several questions train neural networks.

A correct implementation may still take several minutes.

Question 1 should normally finish much faster than the neural-network training questions.

---

# 5. PyTorch Concepts You Need

Before beginning the graded questions, make sure you understand the following ideas.

## 5.1 Tensors

A PyTorch tensor is the primary numerical data structure used throughout this project.

Conceptually, tensors generalize:

```text
scalar
vector
matrix
higher-dimensional array
```

Examples:

```python
torch.tensor([1.0, 2.0, 3.0])
```

and:

```python
torch.ones(4, 8)
```

---

## 5.2 Linear Layers

A linear layer performs an affine transformation:

```text
y = xW + b
```

In PyTorch, a typical layer is created in `__init__`:

```python
self.layer = torch.nn.Linear(input_size, output_size)
```

and used later in `forward`:

```python
output = self.layer(x)
```

Trainable parameters should normally be created once in `__init__`, not recreated every time `forward` is called.

---

## 5.3 ReLU

ReLU is a non-linear activation:

```text
ReLU(x) = max(x, 0)
```

You can apply it using:

```python
torch.relu(x)
```

Without a non-linearity between linear layers, stacking several linear layers is still equivalent to one linear transformation.

The non-linearity is what allows the model to represent more complex functions.

---

## 5.4 Why the Final Layer Often Has No ReLU

For regression, the output may need to be negative.

For classification, the output layer usually returns unrestricted class scores called **logits**.

Therefore, do not automatically place a ReLU after the final linear layer.

This is especially important in Questions 2, 3, 4, 5, and 7.

---

## 5.5 Batching

Rather than processing one example at a time, neural networks usually process a batch.

If one input has dimension:

```text
input_size
```

then a batch of `B` inputs typically has shape:

```text
B × input_size
```

For classification, output scores may have shape:

```text
B × number_of_classes
```

Batching improves efficiency and is required by the provided project infrastructure.

---

## 5.6 DataLoader

Training data is provided through PyTorch datasets.

A typical pattern is:

```python
loader = DataLoader(dataset, batch_size=batch_size, shuffle=True)

for batch in loader:
    x = batch["x"]
    y = batch["label"]
```

The exact code structure may differ depending on the question, but the important point is that each batch contains features and labels.

---

## 5.7 Loss Functions

For regression, use mean squared error:

```python
torch.nn.functional.mse_loss(...)
```

For classification, use cross entropy:

```python
torch.nn.functional.cross_entropy(...)
```

Cross entropy expects model output scores / logits.

Do not manually apply a final softmax before using cross entropy unless a question specifically requires it.

---

## 5.8 Optimizer Training Loop

For gradient-based models, a standard training step is:

```text
1. Clear previous gradients
2. Run the model
3. Compute loss
4. Backpropagate
5. Update parameters
```

Typical PyTorch code:

```python
optimizer.zero_grad()
prediction = model(x)
loss = loss_function(prediction, y)
loss.backward()
optimizer.step()
```

A common optimizer for this project is Adam.

---

# 6. Neural-Network Design and Debugging

Neural-network architecture involves experimentation.

A useful workflow is:

```text
start simple
    ↓
make sure dimensions are correct
    ↓
make sure loss decreases
    ↓
tune learning rate
    ↓
tune hidden size
    ↓
tune batch size
    ↓
add complexity only if necessary
```

Useful general ranges for this project are often:

```text
hidden size:       roughly 100–500
batch size:        roughly 1–128
learning rate:     roughly 0.0001–0.01
hidden layers:     usually 1–3
```

These are starting points, not required answers.

---

## 6.1 Learning Rate

If learning rate is too small:

```text
loss decreases very slowly
```

If learning rate is too large:

```text
loss may oscillate
loss may diverge
loss may become NaN or Infinity
```

Tune learning rate before dramatically increasing model size.

---

## 6.2 Randomness

Neural-network parameters are initialized randomly, and training data may be shuffled.

Therefore, two training runs may not produce exactly the same result.

A model that barely reaches the grading threshold may occasionally fail.

Aim for some margin above the required threshold.

---

## 6.3 Validation vs. Test Accuracy

For some tasks, you can monitor validation accuracy during development.

The autograder may use a separate test set.

Therefore:

```text
validation accuracy ≠ guaranteed test accuracy
```

If the grading threshold is 97%, aim somewhat higher on validation rather than stopping exactly at 97%.

---

# Question 1 – Perceptron

**Points: 20**

## Your Task

Complete the binary perceptron implementation.

You will work with:

```text
models.py
train.py
```

The required components include:

- `PerceptronModel.__init__`
- `PerceptronModel.forward`
- `PerceptronModel.get_prediction`
- `train_perceptron`

---

## The Perceptron Model

The perceptron computes a linear score:

```text
score = w · x
```

The predicted class is:

```text
+1 if score >= 0
-1 otherwise
```

The labels in this problem are:

```text
+1
-1
```

not `0` and `1`.

---

## Weight Parameter

The perceptron weight should be stored as a trainable PyTorch parameter with shape conceptually equivalent to:

```text
1 × dimensions
```

The autograder expects the model to expose the provided weight attribute.

Create the parameter in `__init__`.

Do not recreate it in `forward`.

---

## `forward`

`forward(x)` should compute the dot product between:

```text
input x
and
weight w
```

and return the resulting tensor.

Do not convert the tensor to a normal Python number inside `forward`.

---

## `get_prediction`

Use the sign of the model score.

Conceptually:

```text
if score >= 0:
    return +1
else:
    return -1
```

Make sure the return format matches the starter-code contract.

---

## Perceptron Update Rule

When an example is misclassified, update the weight in the direction:

```text
w ← w + yx
```

where:

```text
y ∈ {-1, +1}
```

If the example is classified correctly, no update is needed.

---

## Training Stopping Condition

Training should continue until an entire pass through the training data contains:

```text
zero mistakes
```

That means the perceptron has achieved 100% training accuracy on the separable dataset.

A good training structure is:

```text
repeat:
    mistakes = 0

    for each training example:
        predict
        if incorrect:
            update
            mistakes += 1

until mistakes == 0
```

---

## Test

```bash
python autograder.py -q q1
```

or:

```bash
python autograder.py -q q1 --no-graphics
```

A correct implementation should normally finish fairly quickly.

If Q1 runs for a very long time, check:

- whether the update direction is correct;
- whether labels are interpreted correctly;
- whether your stopping condition can ever become true.

---

## Common Mistakes

- Using labels `0` and `1` instead of `-1` and `+1`.
- Forgetting to create `self.w`.
- Creating `self.w` with the wrong shape.
- Returning a Python float when a tensor is expected.
- Updating correctly classified examples.
- Updating in the wrong direction.
- Never resetting the per-epoch mistake counter.
- Using gradient descent for the perceptron when the question expects the perceptron update rule.

---

# Question 2 – Non-linear Regression

**Points: 20**

## Your Task

Train a neural network to approximate:

```text
sin(x)
```

over approximately:

```text
[-2π, 2π]
```

You will implement:

```text
RegressionModel
regression_loss
train_regression
```

across:

```text
models.py
losses.py
train.py
```

---

## Why a Linear Model Is Not Enough

A single affine function:

```text
y = ax + b
```

cannot represent the periodic non-linearity of sine.

You therefore need a neural network with at least one non-linear hidden transformation.

A simple architecture may look like:

```text
input
  ↓
Linear
  ↓
ReLU
  ↓
Linear
  ↓
output
```

You may use additional layers if needed, but start simple.

---

## Output Shape

For a batch containing `B` inputs, the model should return:

```text
B × 1
```

Each input `x` should produce one predicted scalar output.

---

## Loss

Use mean squared error.

Conceptually:

```text
MSE = average of (prediction - target)^2
```

Your `regression_loss` function must return a tensor suitable for:

```python
loss.backward()
```

Do not return `None`, a detached Python float, or a manually converted number.

---

## Training

Use a PyTorch optimizer and repeatedly train on batches.

A normal training iteration should:

1. clear gradients;
2. compute predictions;
3. compute regression loss;
4. call `backward`;
5. call optimizer `step`.

---

## Stopping Criterion

There is only one main dataset split for this regression task.

The required performance is an average loss of approximately:

```text
0.02 or lower
```

across the dataset.

You may use training loss as the stopping criterion.

---

## Test

```bash
python autograder.py -q q2
```

Training may take a few minutes.

---

## Debugging

If the model predicts almost a straight line:

- verify that you actually use ReLU or another non-linearity;
- verify that your hidden layer has enough units.

If loss does not decrease:

- check learning rate;
- check optimizer setup;
- check whether gradients are being reset;
- check whether `loss.backward()` is called;
- check whether `optimizer.step()` is called.

If loss becomes `NaN`:

- reduce learning rate;
- verify shapes;
- check for invalid operations.

---

# Question 3 – Digit Classification

**Points: 20**

## Your Task

Train a neural network to classify handwritten digits.

You will implement:

```text
DigitClassificationModel
digitclassifier_loss
train_digitclassifier
```

The dataset contains images of digits:

```text
0, 1, 2, ..., 9
```

---

## Input

Each image has:

```text
28 × 28 = 784
```

pixel values.

For this question, the image is presented as a 784-dimensional input vector.

A batch therefore typically has shape:

```text
B × 784
```

---

## Output

The model should return:

```text
B × 10
```

scores.

Each of the 10 output values corresponds to one digit class.

The predicted class is the index with the highest score.

---

## Final Layer

Do **not** place ReLU after the final linear layer.

The final layer should produce unrestricted logits:

```text
... → Linear → logits
```

not:

```text
... → Linear → ReLU → logits
```

Cross entropy is designed to work with raw logits.

---

## Loss

Use cross entropy:

```python
torch.nn.functional.cross_entropy(...)
```

Do not manually apply softmax before cross entropy.

---

## Training and Validation

This task includes:

- training data;
- validation data;
- hidden test data.

You may use validation accuracy to determine when to stop training.

For example, the dataset object provides a validation-accuracy helper.

---

## Required Accuracy

Your model should achieve at least:

```text
97% test accuracy
```

Because the autograder evaluates a separate test set, it is better to aim for validation accuracy somewhat above 97%.

A practical target is around:

```text
97.5%–98% validation accuracy
```

before stopping.

---

## Architecture

A relatively small feed-forward neural network should be sufficient.

For example:

```text
784
 ↓
hidden layer
 ↓
ReLU
 ↓
optional hidden layer
 ↓
ReLU
 ↓
10 logits
```

Do not make the network unnecessarily enormous.

Larger models train more slowly and are not automatically better.

---

## Test

```bash
python autograder.py -q q3
```

---

## Common Mistakes

- Wrong output dimension.
- ReLU on the final output layer.
- Using MSE instead of cross entropy.
- Applying softmax before cross entropy.
- Stopping immediately at exactly 97% validation accuracy.
- Forgetting `model.train()` / `model.eval()` considerations if you add layers whose behavior depends on mode.
- Using a very large hidden size that makes the autograder excessively slow.

---

# Question 4 – Language Identification

**Points: 20**

## Your Task

Build a model that receives one word and predicts which language it comes from.

The dataset contains words from five languages.

You will implement:

```text
LanguageIDModel
languageid_loss
train_langaugeid
```

using:

```text
models.py
losses.py
train.py
```

Follow the exact function names in the starter code, including any provided spelling.

---

## Why This Task Is Different

Words have different lengths.

A standard fixed-size feed-forward input is therefore inconvenient.

Instead, process the word one character at a time and maintain a hidden representation summarizing the characters seen so far.

This is the basic idea of a recurrent neural network.

---

## Character Inputs

Each character is represented as a one-hot vector.

If the alphabet contains:

```text
num_chars
```

characters, each character input has dimension:

```text
num_chars
```

---

## Recurrent Hidden State

Conceptually:

```text
h1 = f_initial(x0)

h2 = f(h1, x1)

h3 = f(h2, x2)

...

hL = f(hL-1, xL-1)
```

The same trainable transformation should be reused across time steps.

Do not create a brand-new set of weights for every character position.

---

## A Useful Recurrent Structure

One useful form is:

```text
z_t = W_x x_t + W_h h_(t-1)
h_t = nonlinearity(z_t)
```

In PyTorch-layer notation, this might conceptually be:

```text
input transform
+
hidden-state transform
→
ReLU
```

You may build a somewhat richer recurrent transformation if needed.

---

## Batching

The provided infrastructure groups words of compatible length for batching.

That means your hidden state should work with:

```text
B × hidden_size
```

rather than one word at a time.

Avoid writing code that assumes batch size is always 1.

---

## Final Classification

After processing the final character, transform the final hidden state into:

```text
B × number_of_languages
```

logits.

Again, the final output layer should not have ReLU.

---

## Loss

Use cross entropy.

---

## Required Accuracy

Your model must achieve at least:

```text
81% test accuracy
```

The task is harder than digit classification and may require more training epochs.

Do not assume that a model architecture that works well for MNIST will automatically work well for recurrent sequence processing.

---

## Test

```bash
python autograder.py -q q4
```

---

## Common Mistakes

- Ignoring previous hidden state.
- Creating new recurrent layers inside the loop.
- Using different parameters for different word positions.
- Assuming every word has the same global length.
- Forgetting batch dimension.
- Returning only the hidden state instead of language logits.
- Applying ReLU after the final classification layer.
- Training for too few epochs.

---

# Question 5 – Convolutional Neural Networks

**Points: 12**

## Your Task

This question has two parts.

First, implement the provided 2D convolution function.

Then complete a small convolution-based digit classifier.

You will work with:

```text
models.py
losses.py
train.py
```

---

## Why Convolution?

A fully connected layer usually flattens an image:

```text
2D image
→
1D vector
```

Flattening loses explicit local spatial structure.

A convolution instead applies a small kernel to local image regions.

This helps the model recognize patterns such as:

- edges;
- strokes;
- corners;
- local digit shapes.

---

## Basic 2D Convolution

Suppose the kernel is:

```text
k_h × k_w
```

and the input image is:

```text
H × W
```

Without padding, the output size is:

```text
(H - k_h + 1) × (W - k_w + 1)
```

For every output position:

1. take the matching input patch;
2. multiply the patch elementwise by the kernel;
3. sum all products.

---

## Example

For a 2×2 kernel:

```text
[w11 w12
 w21 w22]
```

and the corresponding input patch:

```text
[x11 x12
 x21 x22]
```

the output value is:

```text
x11*w11 + x12*w12 + x21*w21 + x22*w22
```

Repeat this as the kernel slides across the image.

---

## No Padding

For this assignment, you do not need to add zero padding to preserve the original image size.

Therefore, the convolution output should be smaller than the input.

---

## Convolution Function

The starter code guarantees that the provided input matrix is larger than the kernel.

The custom convolution operation is designed to work on one input matrix at a time.

Focus first on mathematical correctness before optimizing performance.

---

## CNN Digit Model

After convolution, the starter infrastructure helps flatten the convolution result.

From that point, you can use ordinary linear layers.

A small model is enough:

```text
image
 ↓
convolution
 ↓
flatten
 ↓
small linear network
 ↓
10 logits
```

You can reuse ideas from Question 3.

---

## Loss

Use cross entropy for the digit classifier.

---

## Required Accuracy

The convolutional classifier is evaluated on a simplified digit dataset.

Your model should achieve at least approximately:

```text
80% accuracy
```

The main conceptual focus of the question is the convolution implementation rather than building a large CNN.

---

## Test

```bash
python autograder.py -q q5
```

The autograder first checks the convolution operation itself and then trains/evaluates the model.

---

## Common Mistakes

- Padding when the question expects valid convolution.
- Using the wrong output dimensions.
- Moving the kernel by the wrong amount.
- Forgetting to sum the elementwise products.
- Flattening before performing the convolution.
- Reusing Question 3 without incorporating the convolution output.
- Using an unnecessarily large model that trains very slowly.

---

# Question 6 – Attention

**Points: 8**

## Your Task

Implement the provided attention block in:

```text
models.py
```

This question introduces **Scaled Dot-Product Attention**.

---

## Query, Key, and Value

The attention block constructs three representations:

```text
Q = query
K = key
V = value
```

In this project, all three are obtained by applying different learned linear transformations to the same input sequence.

Conceptually:

```text
Q = X W_Q
K = X W_K
V = X W_V
```

---

## Attention Scores

Compute:

```text
Q K^T
```

This measures how strongly each sequence position should attend to the others.

Then scale by:

```text
sqrt(d_k)
```

where `d_k` is the key / attention dimension.

So the score matrix is:

```text
(Q K^T) / sqrt(d_k)
```

Scaling helps prevent dot products from becoming excessively large as dimensionality grows.

---

## Softmax

Apply softmax to convert the scores into attention weights.

Conceptually:

```text
attentionWeights
=
softmax(scaledScores)
```

Each row describes how strongly one position attends to allowed positions.

---

## Causal Mask

For sequence generation, a position must not access future characters.

For example, while predicting position 4, the model may attend to:

```text
positions 0, 1, 2, 3, 4
```

but not:

```text
positions 5, 6, ...
```

A causal mask enforces this rule.

The score entries corresponding to forbidden future positions should be suppressed before softmax.

---

## Complete Attention Operation

Conceptually:

```text
Attention(Q,K,V)
=
softmax(
    masked(
        QK^T / sqrt(d_k)
    )
) V
```

Be careful with tensor dimensions.

The batch dimension must remain intact.

---

## Tensor Transpose

For batched tensors, ordinary `.T` may not produce the intended axis ordering.

Follow the dimensional conventions in the starter code and use the provided PyTorch dimension manipulation where appropriate.

---

## Test

```bash
python autograder.py -q q6
```

---

## Common Mistakes

- Forgetting the scale factor.
- Applying softmax over the wrong dimension.
- Applying the mask after softmax.
- Using the wrong mask direction.
- Allowing access to future positions.
- Transposing the batch dimension accidentally.
- Returning attention weights instead of the weighted `V` result.
- Using one shared projection when the starter design expects separate Q/K/V projections.

---

# Question 7 – character-GPT

**Points: 0 – Optional, but Strongly Encouraged**

Question 7 does **not** contribute directly to the required 100-point Project 5 score.

However, you are **strongly encouraged** to complete it.

This optional component connects the attention mechanism from Question 6 to a small transformer-based generative language model.

It is especially relevant to the language-model and LLM topics later in EECE 6399.

---

## Why This Question Is Worth Doing

Questions 1–6 introduce several building blocks:

```text
linear layers
    ↓
non-linear networks
    ↓
sequence modeling
    ↓
attention
```

Question 7 shows how those ideas are assembled into:

```text
transformer blocks
    ↓
next-character prediction
    ↓
autoregressive generation
```

This is conceptually related to the architecture family used by modern GPT-style language models.

---

## Character-Level Modeling

Instead of predicting the next word, this model predicts the next **character**.

For example, given:

```text
To b
```

the model learns a distribution over possible next characters.

Generation repeats this process:

```text
predict next character
        ↓
append it
        ↓
feed longer context back to model
        ↓
predict again
```

This is autoregressive generation.

---

## Training Text

The optional exercise uses a text corpus such as Shakespeare.

Place the required input text file in the location expected by the starter code.

The model is intentionally small enough to experiment with on a CPU.

---

## Transformer Block

A simplified transformer block in this project contains operations conceptually similar to:

```text
input
  ↓
attention
  ↓
residual connection
  ↓
normalization
  ↓
feed-forward transformation
  ↓
residual connection
  ↓
normalization
```

You will complete the relevant `forward` logic in:

```text
gpt_model.py
```

using layers already initialized by the starter code.

---

## Residual Connections

A residual connection adds a block input to a transformed output:

```text
output = input + transformation(input)
```

Residual connections help information and gradients move through deeper networks.

---

## Feed-Forward Part

After attention and normalization, a transformer block also contains a small feed-forward network.

In the simplified project version, follow the exact layers provided in the starter code rather than inventing a completely new architecture.

---

## Full GPT-Style Model

The full model conceptually contains:

```text
input characters
      ↓
embedding
      ↓
transformer block(s)
      ↓
normalization
      ↓
final linear layer
      ↓
next-character logits
```

The final layer should return unrestricted logits.

Do not apply ReLU to the final next-character output layer.

---

## Training

Run:

```bash
python chargpt.py
```

Training a generative model can take time, especially on CPU.

Because this question is not graded, you are encouraged to experiment.

---

## Suggested Experiments

After you get the basic model working, try changing:

- number of transformer blocks;
- embedding dimension;
- attention size;
- context / block length;
- training iterations;
- learning rate;
- input text corpus.

You can also replace the training text with another plain-text corpus and observe how the generated style changes.

---

## What You Should Learn

Even though this question carries no points, you should be able to explain:

- why causal masking is necessary;
- how attention allows tokens to use earlier context;
- what an embedding represents;
- why the final layer predicts one score per possible next character;
- how repeated next-character prediction generates text;
- how transformer blocks build on the attention mechanism from Question 6.

---

# 7. Grading

Project 5 is graded on a **100-point required technical scale**.

| Question | Topic | Points |
|---|---|---:|
| Q1 | Perceptron | 20 |
| Q2 | Non-linear Regression | 20 |
| Q3 | Digit Classification | 20 |
| Q4 | Language Identification | 20 |
| Q5 | Convolutional Neural Networks | 12 |
| Q6 | Attention | 8 |
| Q7 | character-GPT | **0 – Optional, strongly encouraged** |
| **Required Total** |  | **100** |

The local autograder uses the following required technical scale:

| Question | Local Max |
|---|---:|
| Q1 | 5 |
| Q2 | 5 |
| Q3 | 5 |
| Q4 | 5 |
| Q5 | 3 |
| Q6 | 2 |
| **Total** | **25** |

The official EECE 6399 grading system converts the required technical score from:

```text
25 points
```

to:

```text
100 points
```

Question 7 remains outside the required 100-point total.

---

# 8. Submission

Your required Project 5 work must be maintained in your assigned GitHub repository.

The required implementation files are:

```text
models.py
losses.py
train.py
```

If you complete the optional Question 7, also commit your work in:

```text
gpt_model.py
```

Check repository status:

```bash
git status
```

Stage the required files:

```bash
git add models.py losses.py train.py
```

If you completed Q7:

```bash
git add gpt_model.py
```

Commit:

```bash
git commit -m "Update Project 5"
```

Push:

```bash
git push
```

Commit and push regularly.

The official deadline and final submission instructions will be posted in **UTRGV Brightspace**.

---

# 9. Repository and Grading Integrity

The repository contains local testing and dataset infrastructure so you can develop and debug your implementation.

Do not modify grading infrastructure in an attempt to change your score.

Examples include:

```text
autograder.py
backend.py
provided datasets
other grading-related support files
```

The official grading environment is maintained separately.

Official grading uses your required implementation files rather than modified grading infrastructure from your repository.

---

# 10. Academic Integrity

All submitted work must comply with:

- the EECE 6399 syllabus;
- UTRGV academic integrity requirements;
- course rules regarding collaboration;
- course rules regarding generative AI tools.

Unless explicitly authorized, your submitted implementation must represent your own work.

Do not:

- copy another student's implementation;
- distribute complete solutions;
- submit code from previous students;
- submit completed online solutions as your own;
- manipulate the grading system;
- share private grading materials.

You may discuss machine-learning concepts and debugging strategies with classmates, but discussion should not become an exchange of completed code.

---

# 11. Recommended Development Order

Complete the required questions in order:

```text
Q1 Perceptron
        ↓
Q2 Non-linear Regression
        ↓
Q3 Digit Classification
        ↓
Q4 Language Identification
        ↓
Q5 Convolution
        ↓
Q6 Attention
        ↓
Q7 character-GPT
   Optional, strongly encouraged
```

There is a conceptual progression:

```text
linear classifier
        ↓
feed-forward neural network
        ↓
classification
        ↓
sequence model
        ↓
spatial feature model
        ↓
attention
        ↓
transformer language model
```

---

# 12. Recommended Training Workflow

For Questions 2–5:

```text
Implement model dimensions
        ↓
Run a forward pass
        ↓
Verify output shape
        ↓
Implement loss
        ↓
Verify loss is a tensor
        ↓
Implement one optimizer step
        ↓
Confirm loss decreases
        ↓
Train for multiple epochs
        ↓
Check validation / task metric
        ↓
Tune learning rate
        ↓
Tune hidden size / batch size
        ↓
Run autograder
```

Do not immediately build a large architecture before verifying the basic training pipeline.

---

# 13. Debugging Guide

## Autograder says a method returned `None`

This usually means a required starter method still contains a placeholder.

Check:

```text
models.py
losses.py
train.py
```

and make sure every required method returns the expected object.

---

## Shape mismatch

Print tensor shapes temporarily.

For example:

```python
print(x.shape)
print(output.shape)
```

Then compare against the required dimensions.

Common expected shapes include:

```text
Regression:
B × 1

Digit classification:
B × 10

Language classification:
B × number_of_languages
```

Remove unnecessary debugging output before final submission.

---

## Loss does not decrease

Check:

```text
optimizer.zero_grad()
model(x)
loss(...)
loss.backward()
optimizer.step()
```

All five pieces must be correct.

Also check the learning rate.

---

## `loss.backward()` fails

Make sure the loss is still part of the PyTorch computation graph.

Do not convert it to:

```text
float
numpy
list
```

before backpropagation.

---

## Model gets `NaN`

Likely causes include:

- learning rate too high;
- unstable arithmetic;
- incorrect dimension operations;
- unintended division by zero.

Start by reducing learning rate.

---

## Q1 never finishes

The perceptron should stop once an entire pass makes no mistakes.

Check:

- update sign;
- label format;
- mistake counter;
- stopping condition.

---

## Q2 underfits sine

Try:

- larger hidden layer;
- one additional hidden layer;
- different learning rate;
- more training.

First confirm that the model actually contains a non-linearity.

---

## Q3 gets around 10% accuracy

For 10 classes, approximately 10% is random guessing.

Check:

- labels;
- output dimension;
- loss function;
- optimizer;
- whether parameters are registered in the model.

---

## Q3 accuracy stalls below threshold

Try:

- slightly larger hidden representation;
- more epochs;
- learning-rate tuning;
- slightly higher validation stopping target.

Do not automatically make the network enormous.

---

## Q4 fails because of different word lengths

Do not flatten an entire word into one fixed global vector.

Use the recurrent structure provided by the problem.

---

## Q4 recurrent state does not change

Make sure the next hidden state depends on both:

```text
current character
and
previous hidden state
```

---

## Q5 convolution output is the wrong size

For valid convolution:

```text
output_height = input_height - kernel_height + 1
output_width  = input_width  - kernel_width  + 1
```

There is no padding in the required custom operation.

---

## Q6 attention values are wrong

Check in this order:

1. Q/K/V projection shapes.
2. Matrix multiplication.
3. Key transpose dimensions.
4. Division by `sqrt(d_k)`.
5. Causal mask.
6. Softmax dimension.
7. Multiplication by V.

---

## Q6 can see future characters

Your causal mask is reversed or applied incorrectly.

For each position `i`, positions greater than `i` should be inaccessible.

---

## Training takes far too long

Possible causes:

- hidden layers are unnecessarily large;
- too many epochs;
- poor stopping criteria;
- batch size too small;
- repeated expensive work inside the batch loop;
- recreating layers or optimizers repeatedly.

---

# 14. Conceptual Comparison

| Question | Main Idea | Learning Type |
|---|---|---|
| Q1 | Perceptron | Linear classification |
| Q2 | Feed-forward network | Regression |
| Q3 | Feed-forward network | Multi-class classification |
| Q4 | Recurrent network | Sequence classification |
| Q5 | Convolution | Spatial representation learning |
| Q6 | Attention | Context-dependent representation |
| Q7 | Transformer / GPT | Autoregressive generation |

---

# 15. Key Equations and Ideas

## Perceptron

```text
score = w · x

prediction =
+1 if score >= 0
-1 otherwise

if wrong:
w ← w + yx
```

---

## Regression

```text
prediction = neural_network(x)

loss = mean squared error
```

---

## Classification

```text
logits = neural_network(x)

loss = cross entropy(logits, label)
```

---

## Recurrent Update

Conceptually:

```text
h_t = f(x_t, h_(t-1))
```

---

## Convolution

```text
output[i,j]
=
sum of
input patch × kernel
```

---

## Scaled Dot-Product Attention

```text
Attention(Q,K,V)
=
softmax(
    mask(
        QK^T / sqrt(d_k)
    )
) V
```

---

## Autoregressive Generation

```text
context
  ↓
predict next character
  ↓
append prediction
  ↓
new context
  ↓
repeat
```

---

# 16. Final Checklist

Before submitting Project 5, verify that:

- [ ] `PerceptronModel` is implemented.
- [ ] `train_perceptron` reaches zero training mistakes.
- [ ] `RegressionModel` is implemented.
- [ ] `regression_loss` returns a valid tensor.
- [ ] Regression reaches the required loss range.
- [ ] `DigitClassificationModel` returns 10 logits.
- [ ] The digit classifier final layer has no ReLU.
- [ ] `digitclassifier_loss` uses classification loss.
- [ ] Digit classification reaches the required accuracy.
- [ ] `LanguageIDModel` processes variable-length sequences.
- [ ] Recurrent hidden states depend on previous hidden states.
- [ ] `languageid_loss` is implemented.
- [ ] Language identification reaches the required accuracy.
- [ ] The custom convolution operation is correct.
- [ ] The convolutional digit model reaches the required accuracy.
- [ ] The attention block uses Q, K, and V correctly.
- [ ] Attention includes the scaling factor.
- [ ] Attention applies a causal mask.
- [ ] Attention cannot access future positions.
- [ ] `python autograder.py --no-graphics` completes.
- [ ] You investigated all failed required tests.
- [ ] `models.py`, `losses.py`, and `train.py` are committed.
- [ ] Your latest commit is pushed to GitHub.
- [ ] You checked Brightspace for the official deadline.
- [ ] Optional but strongly encouraged: complete Question 7 `character-GPT`.

---

## Optional Q7 Checklist

If you choose to complete Question 7:

- [ ] The transformer block calls the attention module.
- [ ] Residual connections are implemented.
- [ ] Normalization is applied in the required locations.
- [ ] The feed-forward transformation is implemented.
- [ ] The full GPT model applies embedding / input transformation.
- [ ] Transformer blocks are applied in sequence.
- [ ] Final normalization is applied.
- [ ] Final output layer has no ReLU.
- [ ] `python chargpt.py` runs.
- [ ] You can generate character-level text.
- [ ] You experimented with at least one model or training parameter.

---

## Project Framework Notice

This repository uses an educational machine-learning framework adapted for **UTRGV EECE 6399 – AI for Autonomous Systems**.

Course-facing grading, submission procedures, and assignment instructions in this repository are specific to EECE 6399.

Please retain copyright and license notices already included in the distributed source files.
