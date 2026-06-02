# Day 11 – File Ownership Challenge (chown & chgrp)

## Task
Master file and directory ownership in Linux.

- Understand file ownership (user and group)
- Change file owner using `chown`
- Change file group using `chgrp`
- Apply ownership changes recursively

---

## Expected Output
- A markdown file: `day-11-file-ownership.md`
- Screenshots showing ownership changes

---

## Challenge Tasks

### Task 1: Understanding Ownership (10 minutes)

1. Run `ls -l` in your home directory

<img width="516" height="473" alt="image" src="https://github.com/user-attachments/assets/f147a16a-5f3f-4d86-b50c-59eb293b09a2" />
 
2. Identify the **owner** and **group** columns
Owner is ranjeet user and ranjeet group
4. Check who owns your files
files are owned by user ranjeet.

**Format:** `-rw-r--r-- 1 owner group size date filename`

Document: What's the difference between owner and group?
Owner is one specific user with access to the file, level of access is determined by permissions set at file/ directory level.
Group is collecotion of users with common access, used when common access needs to be provided to group of users.
---

### Task 2: Basic chown Operations (20 minutes)

1. Create file `devops-file.txt`
2. Check current owner: `ls -l devops-file.txt`

<img width="501" height="81" alt="image" src="https://github.com/user-attachments/assets/963718ef-e34b-4b96-8a2c-ef9b9dae217d" />

3. Change owner to `tokyo` (create user if needed)

<img width="493" height="80" alt="image" src="https://github.com/user-attachments/assets/21f0ee19-abff-47ae-a659-437b9a02e22a" />

4. Change owner to `berlin`
5. Verify the changes

<img width="480" height="57" alt="image" src="https://github.com/user-attachments/assets/fab028f7-b64e-42d8-a2a1-8ad8c0800bea" />


**Try:**
```bash
sudo chown tokyo devops-file.txt
```

---

### Task 3: Basic chgrp Operations (15 minutes)

1. Create file `team-notes.txt`
2. Check current group: `ls -l team-notes.txt`
3. Create group: `sudo groupadd heist-team`

<img width="478" height="74" alt="image" src="https://github.com/user-attachments/assets/1b396e72-84c9-4ef1-8e2c-3328421faf98" />

4. Change file group to `heist-team`

5. Verify the change

<img width="517" height="78" alt="image" src="https://github.com/user-attachments/assets/db44cfe1-85c2-4538-9565-6836992fff17" />

---

### Task 4: Combined Owner & Group Change (15 minutes)

Using `chown` you can change both owner and group together:

1. Create file `project-config.yaml`
2. Change owner to `professor` AND group to `heist-team` (one command)

<img width="719" height="150" alt="image" src="https://github.com/user-attachments/assets/3ee736ea-9cb6-4a22-9a1d-360571450f27" />

3. Create directory `app-logs/`
4. Change its owner to `berlin` and group to `heist-team`

<img width="505" height="180" alt="image" src="https://github.com/user-attachments/assets/0b62af5c-f337-48b6-a294-a441b7363fed" />


**Syntax:** `sudo chown owner:group filename`

---

### Task 5: Recursive Ownership (20 minutes)

1. Create directory structure:

   mkdir -p heist-project/vault
   mkdir -p heist-project/plans
   touch heist-project/vault/gold.txt
   touch heist-project/plans/strategy.conf

   <img width="472" height="77" alt="image" src="https://github.com/user-attachments/assets/4055034c-8cbe-4c81-beca-a0d571849f84" />

2. Create group `planners`: `sudo groupadd planners`

<img width="333" height="59" alt="image" src="https://github.com/user-attachments/assets/72008003-947d-43a0-802e-c96eb5e4427e" />

4. Change ownership of entire `heist-project/` directory:
   - Owner: `professor`
   - Group: `planners`
   - Use recursive flag (`-R`)

<img width="537" height="118" alt="image" src="https://github.com/user-attachments/assets/e182750a-152d-48f8-95ce-97131a814988" />

5. Verify all files and subdirectories changed: `ls -lR heist-project/`

<img width="533" height="115" alt="image" src="https://github.com/user-attachments/assets/6ce04a9e-1064-4366-afa9-6db122d23cb8" />

---

### Task 6: Practice Challenge (20 minutes)

1. Create users: `tokyo`, `berlin`, `nairobi` (if not already created)

<img width="428" height="76" alt="image" src="https://github.com/user-attachments/assets/146109ff-2270-4c83-b65f-3c62866c2cd2" />

3. Create groups: `vault-team`, `tech-team`

<img width="350" height="106" alt="image" src="https://github.com/user-attachments/assets/afe3ffb2-00b1-4109-9275-f5f8c530740b" />

5. Create directory: `bank-heist/`
6. Create 3 files inside:
   
   touch bank-heist/access-codes.txt
   touch bank-heist/blueprints.pdf
   touch bank-heist/escape-plan.txt

<img width="525" height="204" alt="image" src="https://github.com/user-attachments/assets/269ce253-857c-4149-b59f-5b0e7e28cc03" />

7. Set different ownership:
   - `access-codes.txt` → owner: `tokyo`, group: `vault-team`
   - `blueprints.pdf` → owner: `berlin`, group: `tech-team`
   - `escape-plan.txt` → owner: `nairobi`, group: `vault-team`

**Verify:** `ls -l bank-heist/`

<img width="616" height="386" alt="image" src="https://github.com/user-attachments/assets/f9e86f14-25fd-4379-b79f-b87594841ef6" />

---

## Key Commands Reference

```bash
# View ownership
ls -l filename

# Change owner only
sudo chown newowner filename

# Change group only
sudo chgrp newgroup filename

# Change both owner and group
sudo chown owner:group filename

# Recursive change (directories)
sudo chown -R owner:group directory/

# Change only group with chown
sudo chown :groupname filename
```

---

## Hints

- Most `chown`/`chgrp` operations need `sudo`
- Use `-R` flag for recursive directory changes
- Always verify with `ls -l` after changes
- User must exist before using in `chown`
- Group must exist before using in `chgrp`/`chown`

---

## Documentation

Create `day-11-file-ownership.md`:

```markdown
# Day 11 Challenge

## Files & Directories Created
[list all files/directories]

## Ownership Changes
[before/after for each file]

Example:
- devops-file.txt: user:user → tokyo:heist-team

## Commands Used
[your commands here]

## What I Learned
[3 key points about file ownership]
```

---

## Troubleshooting

**Permission denied?**
- Use `sudo` for chown/chgrp operations

**Group doesn't exist?**
- Create it first: `sudo groupadd groupname`

**User doesn't exist?**
- Create it first: `sudo useradd username`

---

## Why This Matters for DevOps

In real DevOps scenarios, you need proper file ownership for:

- Application deployments
- Shared team directories
- Container file permissions
- CI/CD pipeline artifacts
- Log file management

---
#DevOpsKaJosh
#TrainWithShubham
```

Happy Learning
**TrainWithShubham**
