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


