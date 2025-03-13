# NewPythonApp

Follow these steps to create a new Python project from scratch using **Python 3** in **Visual Studio Code** on **Mac**.

---

### Check Python Version and Update if Needed

Check your installed Python version:
```bash
python3 --version
```
(Optional) Update Python if outdated:

If your version is outdated, update it using Homebrew:
```bash
brew upgrade python
```

---

## Install Python Extensions in VS Code

Install the following extensions from the VS Code Marketplace:

- **[Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)**


---

## 🚀 Quick Setup Script
Run this script to create a new Python project:
```bash
cd ~/Developer            
mkdir MyPythonProject     
cd MyPythonProject      
python3 -m venv .venv    
source .venv/bin/activate
touch .gitignore
touch main.py
```

Verify:

```bash
ls -l
python3 --version
python3 main.py
```

---

### Configure VS Code for Python Development
If VS Code does not detect the correct Python interpreter, select it manually:
- Open the Command Palette (`Cmd + Shift + P`).
- Search for **Python: Select Interpreter**.
- Choose the virtual environment inside your project: `.venv/bin/python3`.

Verify configuration:

```bash
python3 --version
python3 main.py
```

---

## Initialize Git Repository
If you plan to use Git for version control, initialize a repository:
```bash
git init
```
Create a `.gitignore` file to exclude unnecessary files:
```bash
echo '.venv/
__pycache__/
*.pyc' > .gitignore
```
Commit the initial setup:
```bash
git add .
git commit -m "Initial commit"
```

---

✅ **All Set!**
