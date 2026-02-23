---
tags:
  - language
  - python
  - textEditor
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses YAMl.
Status: Done
Started: 2025-03-10
EditDate: 2025-03-10
Relates: 
Peer Reviewed: 0
dg-publish: false
---
To create a virtual environment in **VS Code** for Python, follow these steps:

#todo/Low/Dev 
- [ ] [PEP 20 – The Zen of Python \| peps.python.org](https://peps.python.org/pep-0020/)
### **1. Open VS Code and Your Project Folder**

Make sure you're inside your project folder in VS Code.

### **2. Open the Terminal in VS Code**

- On **Windows/Linux**: Press `Ctrl + ~` (tilde)
- On **Mac**: Press `Cmd + ~`
- Or go to **View** → **Terminal**

### **3. Create a Virtual Environment**

Run the following command in the terminal:

#### **Windows**

```bash
python -m venv venv
```

#### **Mac/Linux**

```bash
python3 -m venv venv
```

This will create a **`venv`** folder inside your project.

### **4. Activate the Virtual Environment**

After creating it, activate the environment based on your OS:

#### **Windows (Command Prompt)**

```bash
venv\Scripts\activate
```

#### **Windows (PowerShell)**

```powershell
venv\Scripts\Activate.ps1
```

_(If you get an execution policy error, run: `Set-ExecutionPolicy Unrestricted -Scope Process` in PowerShell.)_

#### **Mac/Linux**

```bash
source venv/bin/activate
```

After activation, your terminal prompt should change, showing `(venv)`, indicating that the virtual environment is active.

### **5. Select the Virtual Environment in VS Code**

1. **Open the Command Palette** (`Ctrl + Shift + P` or `Cmd + Shift + P` on Mac).
2. Search for **"Python: Select Interpreter"** and click on it.
3. Choose the interpreter inside the `venv` folder (e.g., `./venv/bin/python` or `.\venv\Scripts\python.exe` on Windows).

### **6. Install Packages in the Virtual Environment**

Once activated, install dependencies inside the virtual environment:

```bash
pip install -r requirements.txt
```

or install packages manually:

```bash
pip install <package-name>
```

### **7. Deactivate the Virtual Environment**

To exit the virtual environment, run:

```bash
deactivate
```

Now your Python project is set up with an isolated virtual environment in **VS Code**! Let me know if you need any help.