# Day 18 – Shell Scripting: Functions & intermediate Concepts

## Task
Write cleaner, reusable scripts — learn functions, strict mode, and real-world patterns.

You will:
- Write and call **functions**
- Use **`set -euo pipefail`** for safer scripts
- Work with **return values** and **local variables**
- Build an intermediate script

---

## Expected Output
- A markdown file: `day-18-scripting.md`
- All scripts you write during the tasks

---

## Challenge Tasks

### Task 1: Basic Functions
1. Create `functions.sh` with:
   - A function `greet` that takes a name as argument and prints `Hello, <name>!`
   - A function `add` that takes two numbers and prints their sum
   - Call both functions from the script
  
     <img width="371" height="246" alt="image" src="https://github.com/user-attachments/assets/84cc9435-e687-48e1-a6c5-cc4a11534e9c" />
     <br>
     <img width="298" height="74" alt="image" src="https://github.com/user-attachments/assets/55539e18-2b2f-4e0a-ba3d-8cc38dd6a7d1" />

---

### Task 2: Functions with Return Values
1. Create `disk_check.sh` with:
   - A function `check_disk` that checks disk usage of `/` using `df -h`
   - A function `check_memory` that checks free memory using `free -h`
   - A main section that calls both and prints the results
  
     <img width="375" height="286" alt="image" src="https://github.com/user-attachments/assets/e1b3f558-0641-4761-b591-5c2e717b52d0" />
      <br>
     <img width="572" height="201" alt="image" src="https://github.com/user-attachments/assets/a1cb9eaf-9066-4253-a5c8-f21260571afa" />


---

### Task 3: Strict Mode — `set -euo pipefail`
1. Create `strict_demo.sh` with `set -euo pipefail` at the top
2. Try using an **undefined variable** — what happens with `set -u`?
   - if set -u is set and undefined variable is used in the script, script execution fail with an error "./strict_demo.sh: line 4: name: unbound variable"
   - if set -u is not used, script execution completes and undefined variable in put as blank. 
   
   <img width="344" height="258" alt="image" src="https://github.com/user-attachments/assets/6f652270-0153-43fb-ac0d-3829501822f4" />

4. Try a command that **fails** — what happens with `set -e`?
   <br> <img width="607" height="393" alt="image" src="https://github.com/user-attachments/assets/39d8cf16-895e-4b79-bd27-646ca4306a94" />
   <br> <img width="541" height="304" alt="image" src="https://github.com/user-attachments/assets/513174d1-6828-47d6-a4fd-9fa780583996" />
   <br>one more example<br>
   with set -e <br><img width="416" height="224" alt="image" src="https://github.com/user-attachments/assets/630893fe-21a2-4a33-886f-b5d0cff5cc3f" /><br>
   without set -e <br><img width="410" height="190" alt="image" src="https://github.com/user-attachments/assets/e8ce0524-d54d-439f-9a8d-8c716f66d511" />

6. Try a **piped command** where one part fails — what happens with `set -o pipefail`?

#### What does each flag do?
- `set -e` →
- `set -u` →
- `set -o pipefail` →

##### `set -e`

- Causes the script to exit immediately if a command returns a non-zero (error) exit status.
- Helps prevent the script from continuing when a command fails.

**Example:**

```bash
set -e

cp file1.txt /tmp/
cp missing.txt /tmp/   # Fails here
echo "Done"            # Not executed
```

**Memory Trick:**

> `e` = Exit on Error

---

##### `set -u`

- Causes the script to exit if an undefined (unset) variable is referenced.
- Does **not** fail when a variable is defined but contains an empty value.

**Example (Fails):**

```bash
set -u

echo "$NAME"
```

Output:

```text
bash: NAME: unbound variable
```

**Example (Works):**

```bash
set -u

NAME=""
echo "$NAME"
```

This works because `NAME` is defined, even though it is empty.

**Memory Trick:**

> `u` = Undefined Variable Check

---

#### Common Production Usage

```bash
set -euo pipefail
```

##### What Each Option Does

```bash
set -e
```

> Exit immediately when a command fails.

```bash
set -u
```

> Exit when an undefined variable is used.

```bash
set -o pipefail
```

> A pipeline fails if any command within the pipeline fails.

**Example:**

```bash
grep "error" missing.log | wc -l
```

Without `pipefail`, the pipeline may still succeed even if `grep` fails.

With `pipefail`, the entire pipeline fails.

---

#### Interview Answer

> `set -e` makes the shell script exit immediately when a command returns a non-zero exit code. `set -u` makes the script exit when an undefined variable is referenced. These flags help make shell scripts safer and easier to troubleshoot.

---

### Task 4: Local Variables
1. Create `local_demo.sh` with:
   - A function that uses `local` keyword for variables
   - Show that `local` variables don't leak outside the function
   - Compare with a function that uses regular variables

---

### Task 5: Build a Script — System Info Reporter
Create `system_info.sh` that uses functions for everything:
1. A function to print **hostname and OS info**
2. A function to print **uptime**
3. A function to print **disk usage** (top 5 by size)
4. A function to print **memory usage**
5. A function to print **top 5 CPU-consuming processes**
6. A `main` function that calls all of the above with section headers
7. Use `set -euo pipefail` at the top

Output should look clean and readable.

---

## Hints
- Function syntax: `function_name() { ... }`
- Local vars: `local MY_VAR="value"`
- Strict mode: `set -euo pipefail` as first line after shebang
- Pass args to functions: `greet "Shubham"` → access as `$1` inside
- `$?` gives the exit code of last command

---

## Documentation

Create `day-18-scripting.md` with:
- Each script's code and output
- Explanation of `set -euo pipefail`
- What you learned (3 key points)

---

## Submission
1. Add your scripts and `day-18-scripting.md` to `2026/day-18/`
2. Commit and push to your fork

---

## Learn in Public

Share what you learned about shell functions and strict mode on LinkedIn.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
