# Day 38 – YAML Basics

## Task
Before writing a single CI/CD pipeline, you need to get comfortable with **YAML** — the language every pipeline is written in.

You will:
- Understand YAML syntax and rules
- Write YAML files by hand
- Validate them

---

## Expected Output
- A markdown file: `day-38-yaml.md`
- YAML files you create during the tasks

---

## Challenge Tasks

### Task 1: Key-Value Pairs
Create `person.yaml` that describes yourself with:
- `name`
- `role`
- `experience_years`
- `learning` (a boolean)
<br><img width="480" height="85" alt="image" src="https://github.com/user-attachments/assets/1c56bcb0-b728-46ff-a435-503966710ec3" />

**Verify:** Run `cat person.yaml` — does it look clean? No tabs?

---

### Task 2: Lists
Add to `person.yaml`:
- `tools` — a list of 5 DevOps tools you know or are learning
  <br><img width="486" height="180" alt="image" src="https://github.com/user-attachments/assets/3dd06168-5638-492a-9df4-82a70bc1fc81" />

- `hobbies` — a list using the inline format `[item1, item2]`
<br><img width="481" height="184" alt="image" src="https://github.com/user-attachments/assets/6c5932bb-1fac-4807-b6b4-a373fbc1494a" />

Write in your notes: What are the two ways to write a list in YAML?
<br>1. Block Style (Using Dashes): This style uses a new line for each item, preceded by a hyphen (-) and a space. It is the most common and readable format.yaml
<br>fruits:
<br>  - Apple
<br>  - Banana
<br>  - Orange

<br>2. Flow Style (Using Square Brackets): This style writes all items on a single line enclosed in square brackets [ ] and separated by commas. It is compact and looks identical to JSON array syntax.yaml
<br>fruits: [Apple, Banana, Orange] 

---

### Task 3: Nested Objects
Create `server.yaml` that describes a server:
- `server` with nested keys: `name`, `ip`, `port`
  <br><img width="480" height="88" alt="image" src="https://github.com/user-attachments/assets/e5a8fef6-f4d3-42cd-8121-8e0adb0dc2e8" />

- `database` with nested keys: `host`, `name`, `credentials` (nested further: `user`, `password`)
<br><img width="486" height="187" alt="image" src="https://github.com/user-attachments/assets/417f1848-d8e5-4eb0-a37c-96278cf25197" />

**Verify:** Try adding a tab instead of spaces — what happens when you validate it?
<br><img width="551" height="452" alt="image" src="https://github.com/user-attachments/assets/5fe73b88-a6fd-427d-b528-34aaa7dec303" />

---

### Task 4: Multi-line Strings
In `server.yaml`, add a `startup_script` field using:
1. The `|` block style (preserves newlines)
2. The `>` fold style (folds into one line)

Write in your notes: When would you use `|` vs `>`?

---

### Task 5: Validate Your YAML
1. Install `yamllint` or use an online validator
2. Validate both your YAML files
3. Intentionally break the indentation — what error do you get?
4. Fix it and validate again

---

### Task 6: Spot the Difference
Read both blocks and write what's wrong with the second one:

```yaml
# Block 1 - correct
name: devops
tools:
  - docker
  - kubernetes
```

```yaml
# Block 2 - broken
name: devops
tools:
- docker
  - kubernetes
```

---

## Hints
- YAML uses **spaces only** — never tabs
- Indentation is everything — 2 spaces is standard
- Strings don't need quotes unless they contain special characters (`:`, `#`, etc.)
- `true`/`false` are booleans, `"true"` is a string
- Validate online: yamllint.com

---

## Documentation
Create `day-38-yaml.md` with:
- Your YAML files
- What you learned (3 key points)

---

## Submission
1. Add your YAML files and `day-38-yaml.md` to `2026/day-38/`
2. Commit and push to your fork

---

## Learn in Public
Share your YAML "aha moment" on LinkedIn — the tab vs space mistake gets everyone.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
