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

The Python extension will automatically install the following extensions by default to provide the best Python development experience in VS Code:

- **Pylance** - to provide performant Python language support.
- **Python Debugger** - to provide a seamless debug experience with debugpy.

---

## 🚀 Quick Setup Script
Run this script to create a new Python app:
```bash
cd ~/Developer              
mkdir MyNewPythonApp       
cd MyNewPythonApp          
python3 -m venv .venv       
source .venv/bin/activate   
touch main.py               
echo 'import sys

def main():
    print("My New Python App Running!")

if __name__ == "__main__":
    main()' > main.py 
```
Download recommended .gitignore for Python:
(It’s hosted in GitHub’s official gitignore repository: GitHub/gitignore.)
```bash
curl -o .gitignore https://raw.githubusercontent.com/github/gitignore/main/Python.gitignore 
``` 

Verify configuration:
```bash
ls -a
python3 --version
python3 main.py
```

Open the project:
```bash
code .
```

Configure VS Code for Python Development:
If VS Code does not detect the correct Python interpreter, select it manually.
- Open the Command Palette (`Cmd + Shift + P`).
- Search for **Python: Select Interpreter**.
- Choose the virtual environment inside your project: `.venv/bin/python3`.

Verify configuration:
```bash
python3 --version
python3 main.py
```

Initialize Git:
```bash
git init
git add .
git commit -m "Initial commit with Python .gitignore"
```

---


✅ **All Set!**
