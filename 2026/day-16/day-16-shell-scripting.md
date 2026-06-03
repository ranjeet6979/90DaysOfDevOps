# Day 16 – Shell Scripting Basics

## Task
Start your shell scripting journey — learn the fundamentals every script needs.

You will:
- Understand **shebang** (`#!/bin/bash`) and why it matters
- Work with **variables**, **echo**, and **read**
- Write basic **if-else** conditions

---

## Expected Output
- A markdown file: `day-16-shell-scripting.md`
- All scripts you write during the tasks

---

## Challenge Tasks

### Task 1: Your First Script
1. Create a file `hello.sh`
2. Add the shebang line `#!/bin/bash` at the top
3. Print `Hello, DevOps!` using `echo`
4. Make it executable and run it

<img width="431" height="160" alt="image" src="https://github.com/user-attachments/assets/2befe9a0-7c6a-4fbe-92fe-d6cb3a463141" />

```bash
chmod +x hello.sh
./hello.sh
```

**Document:** What happens if you remove the shebang line?
if shebag line is removed, script will be executed using default shell of the user running the script, in screenshot below, default shell of the user running the script was /bin/bash hence ran with the bash interpreter.

<img width="311" height="133" alt="image" src="https://github.com/user-attachments/assets/dcd60e55-20e1-490e-8cab-018cceeaefeb" />

---

### Task 2: Variables
1. Create `variables.sh` with:
   - A variable for your `NAME`
   - A variable for your `ROLE` (e.g., "DevOps Engineer")
   - Print: `Hello, I am <NAME> and I am a <ROLE>`
     
     <img width="353" height="83" alt="image" src="https://github.com/user-attachments/assets/00e122c9-cf5b-4961-85a4-ad784055f4c8" />

     <img width="397" height="101" alt="image" src="https://github.com/user-attachments/assets/d9da425b-dda2-439e-b75e-739ba8dc3022" />

2. Try using single quotes vs double quotes — what's the difference?
    - running with single quote and double quote gives same output
---

### Task 3: User Input with read
1. Create `greet.sh` that:
   - Asks the user for their name using `read`
   - Asks for their favourite tool
   - Prints: `Hello <name>, your favourite tool is <tool>`

     <img width="436" height="181" alt="image" src="https://github.com/user-attachments/assets/1ddfbd0d-1109-4d55-8e4e-bcce28638f60" />

---

### Task 4: If-Else Conditions
1. Create `check_number.sh` that:
   - Takes a number using `read`
   - Prints whether it is **positive**, **negative**, or **zero**

2. Create `file_check.sh` that:
   - Asks for a filename
   - Checks if the file **exists** using `-f`
   - Prints appropriate message
     
    <img width="376" height="359" alt="image" src="https://github.com/user-attachments/assets/aadc711f-319a-4c82-8685-44f80195a8ed" />

---

### Task 5: Combine It All
Create `server_check.sh` that:
1. Stores a service name in a variable (e.g., `nginx`, `sshd`)
2. Asks the user: "Do you want to check the status? (y/n)"
3. If `y` — runs `systemctl status <service>` and prints whether it's **active** or **not**
4. If `n` — prints "Skipped."

   <img width="1349" height="702" alt="image" src="https://github.com/user-attachments/assets/c8cff7ee-c9c5-47d8-81a9-a3959c0c61a0" />

   <img width="587" height="488" alt="image" src="https://github.com/user-attachments/assets/38fa50f7-e087-444b-a049-9434cf6fcf33" />

---

## Hints
- Shebang: `#!/bin/bash` tells the system which interpreter to use
- Variables: `NAME="Shubham"` (no spaces around `=`)
- Read: `read -p "Enter name: " NAME`
- If syntax: `if [ condition ]; then ... elif ... else ... fi`
- File check: `if [ -f filename ]; then`

---

## Documentation

Create `day-16-shell-scripting.md` with:
- Each script's code and output
- What you learned (3 key points)

---

## Submission
1. Add your scripts and `day-16-shell-scripting.md` to `2026/day-16/`
2. Commit and push to your fork

---

## Learn in Public

Share your first shell scripts on LinkedIn.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
