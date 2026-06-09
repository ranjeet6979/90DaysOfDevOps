# Day 22 – Introduction to Git: Your First Repository

## Task

Today marks the beginning of your Git journey. Git is the backbone of modern DevOps — every tool, pipeline, and workflow revolves around version control. Before diving into advanced concepts, you need to get comfortable with the basics by doing.

You will:
- Understand what Git is and why it matters
- Set up your first Git repository from scratch
- Start building a living document of Git commands

---

## Expected Output
- A local Git repository with a clean commit history
- A file called `git-commands.md` that you will keep updating in future days
- A file called `day-22-notes.md` with your answers

---

## Challenge Tasks

### Task 1: Install and Configure Git
1. Verify Git is installed on your machine
   
   <img width="267" height="49" alt="image" src="https://github.com/user-attachments/assets/7db9152a-6476-4ffd-859c-d7851194422a" />

3. Set up your Git identity — name and email

   <img width="818" height="140" alt="image" src="https://github.com/user-attachments/assets/ddc47f42-b3ca-4ecc-b406-d41c73e51066" />


   
5. Verify your configuration

---

### Task 2: Create Your Git Project
1. Create a new folder called `devops-git-practice`
2. Initialize it as a Git repository

   <img width="733" height="110" alt="image" src="https://github.com/user-attachments/assets/fbee2369-cc89-4296-b436-2bf9464a3b77" />

3. Check the status — read and understand what Git is telling you

   tell it is pointing to master branch, no commits done yet and no files in staging area.

   <img width="525" height="106" alt="image" src="https://github.com/user-attachments/assets/d70e4ad7-6512-49ed-be3f-313de3038028" />

   
4. Explore the hidden `.git/` directory — look at what's inside

<img width="534" height="298" alt="image" src="https://github.com/user-attachments/assets/5fa9e010-b5e0-4c49-a6f6-5a48069ae9e9" />

---

### Task 3: Create Your Git Commands Reference
1. Create a file called `git-commands.md` inside the repo
2. Add the Git commands you've used so far, organized by category:
   - **Setup & Config**
   - **Basic Workflow**
   - **Viewing Changes**
3. For each command, write:
   - What it does (1 line)
   - An example of how to use it

---

### Task 4: Stage and Commit
1. Stage your file
2. Check what's staged
3. Commit with a meaningful message
4. View your commit history

---

### Task 5: Make More Changes and Build History
1. Edit `git-commands.md` — add more commands as you discover them
2. Check what changed since your last commit
3. Stage and commit again with a different, descriptive message
4. Repeat this process at least **3 times** so you have multiple commits in your history
5. View the full history in a compact format

   <img width="533" height="128" alt="image" src="https://github.com/user-attachments/assets/7b1cf6ea-f211-434a-a27a-5f531d13bbe2" />

---

### Task 6: Understand the Git Workflow
Answer these questions in your own words (add them to a `day-22-notes.md` file):
1. What is the difference between `git add` and `git commit`?
   git add: Copies changes from your working directory into the staging area.
   git commit: Permanently saves those staged changes into your local repository history.
2. What does the **staging area** do? Why doesn't Git just commit directly?
   acts as buffer layer before commiting changes to git repo. Only specific changes can be staged (staged can be multiple time). Once all required changes are staged one or multiple commits can be done to ensure each commits has only required changes.
3. What information does `git log` show you
   
   <img width="469" height="513" alt="image" src="https://github.com/user-attachments/assets/a0fdf887-550b-4212-a97d-8b42642bd2e9" />

   Commit ID: Show commit ID or hash for each commit
   Author: shows git username and email ID configured at system level.
   Date and Time about for each commit with commit message.

4. What is the `.git/` folder and what happens if you delete it?
   The .git folder is a hidden directory that stores all version control information for a Git repository, and deleting it will remove the repository’s history and version tracking.

5. What is the difference between a **working directory**, **staging area**, and **repository**?
   In Git, In working directory we edit files, the staging area is a stage before commit stage, and the repository has complete history of the project.
---

## Ongoing Task

**Keep updating `git-commands.md` every day** as you learn new Git commands in the upcoming days. This will become your personal Git reference. Maintain a clean commit history — one commit per update with a clear message.

---

## Hints
- All you need today are about 8-10 Git commands — Google them, try them, break things
- Read what `git status` tells you — it's your best friend
- Use `man git-<command>` or `git <command> --help` to explore

---

## Submission
1. Share a screenshot of your `git log --oneline` output showing multiple commits
2. Add your `day-22-notes.md` to `2026/day-22/`
3. Commit and push to your fork
4. Add your submission for Community Builder of the week on discord

---

## Learn in Public

Share your first Git repo and commit history on LinkedIn.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
