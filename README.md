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
import json
import os
import subprocess
import sys

# Define project structure
PROJECT_NAME = "PythonDemoApp"
SRC_FOLDER = "src"
MAIN_FILE = "main.py"
CONTROLLER_FILE = "controller.py"
TEST_FOLDER = "tests"
TEST_MAIN_FILE = "test_main.py"
TEST_CONTROLLER_FILE = "test_controller.py"

# Step 1: Create the project folder structure
os.makedirs(PROJECT_NAME, exist_ok=True)
os.chdir(PROJECT_NAME)

# Create the main source and test folders
os.makedirs(SRC_FOLDER, exist_ok=True)
os.makedirs(TEST_FOLDER, exist_ok=True)

# Ensure src and tests are recognized as packages
open(os.path.join(SRC_FOLDER, "__init__.py"), "w").close()
open(os.path.join(TEST_FOLDER, "__init__.py"), "w").close()

# Step 2: Set up a virtual environment
subprocess.run([sys.executable, "-m", "venv", "env"])

# Step 3: Create the main application file
main_content = """from src.controller import greet  # ✅ Import from controller

def main():
    name = input("Enter your name: ")
    print(greet(name))

if __name__ == "__main__":
    main()
"""

with open(os.path.join(SRC_FOLDER, MAIN_FILE), "w") as f:
    f.write(main_content)

# Step 4: Create the controller file
controller_content = """def greet(name):
    \"\"\"Returns a greeting message.\"\"\"
    return f"Hello, {name}! Welcome to PythonDemoApp 🚀"
"""

with open(os.path.join(SRC_FOLDER, CONTROLLER_FILE), "w") as f:
    f.write(controller_content)

# Step 5: Create test files
test_main_content = """import unittest
from src.controller import greet

class TestMainFunction(unittest.TestCase):
    def test_greet(self):
        self.assertEqual(greet("Alice"), "Hello, Alice! Welcome to PythonDemoApp 🚀")

if __name__ == '__main__':
    unittest.main()
"""

with open(os.path.join(TEST_FOLDER, TEST_MAIN_FILE), "w") as f:
    f.write(test_main_content)

test_controller_content = """import unittest
from src.controller import greet

class TestController(unittest.TestCase):
    def test_greet(self):
        self.assertEqual(greet("Bob"), "Hello, Bob! Welcome to PythonDemoApp 🚀")

if __name__ == '__main__':
    unittest.main()
"""

with open(os.path.join(TEST_FOLDER, TEST_CONTROLLER_FILE), "w") as f:
    f.write(test_controller_content)

# Step 6: Create a requirements.txt file
with open("requirements.txt", "w") as f:
    f.write("# Add your dependencies here\n")

# Step 7: Set up VS Code configuration
VSCODE_FOLDER = ".vscode"
SETTINGS_FILE = os.path.join(VSCODE_FOLDER, "settings.json")
os.makedirs(VSCODE_FOLDER, exist_ok=True)

vscode_settings = {
    "python.testing.unittestEnabled": True,
    "python.testing.pytestEnabled": False,
    "python.testing.unittestArgs": ["-v", "-s", "./tests", "-p", "test_*.py"],
    "python.defaultInterpreterPath": os.path.abspath(
        "env/bin/python" if sys.platform != "win32" else "env\\Scripts\\python.exe"
    ),
    "terminal.integrated.env.osx": {"PYTHONPATH": "${workspaceFolder}"},
    "terminal.integrated.env.linux": {"PYTHONPATH": "${workspaceFolder}"},
    "terminal.integrated.env.windows": {"PYTHONPATH": "${workspaceFolder}"},
}

with open(SETTINGS_FILE, "w") as f:
    json.dump(vscode_settings, f, indent=4)


# Step 8: Display menu for user actions
def show_menu():
    print("\n***************************************")
    print("🎯 What would you like to do next?")
    print("1️⃣ Activate the virtual environment")
    print("2️⃣ Run tests")
    print("3️⃣ Exit")
    print("***************************************")


while True:
    show_menu()
    choice = input("👉 Enter your choice (1-3): ").strip()

    if choice == "1":
        print("\n🚀 To activate the virtual environment, run:")
        if sys.platform == "win32":
            print("   env\\Scripts\\activate")
        else:
            print("   source env/bin/activate")

    elif choice == "2":
        print("\n🔍 Running tests...")
        subprocess.run([sys.executable, "-m", "unittest", "discover", "tests"])

    elif choice == "3":
        print("\n👋 Exiting setup. Happy coding! 🚀")
        break

    else:
        print("\n❌ Invalid choice. Please enter 1, 2, or 3.")

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
git log
git status
```

---


✅ **All Set!**
