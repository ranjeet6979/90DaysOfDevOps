## Challenge Tasks

### Task 1: Create Users (20 minutes)

Create three users with home directories and passwords:
- `tokyo`
- `berlin`
- `professor`
  
<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/ec326aba-284e-4367-85bc-345e95869b3d" />

**Verify:** Check `/etc/passwd` and `/home/` directory

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/7d53e19f-e3f6-41c2-bce1-f06449847a1d" />

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/ad1da147-1e24-413c-b73d-572db8b94131" />

---

### Task 2: Create Groups (10 minutes)

Create two groups:
- `developers`
- `admins`

**Verify:** Check `/etc/group`

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/2130710f-ad00-4314-9d7f-cfa1e92f89c5" />

---

### Task 3: Assign to Groups (15 minutes)

Assign users:
- `tokyo` → `developers`
- `berlin` → `developers` + `admins` (both groups)
- `professor` → `admins`

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/0d47ebc1-f7fc-4222-b9aa-32e70a5512ca" />


**Verify:** Use appropriate command to check group membership

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/fcd43f18-d6cc-4083-be4d-1d333df38e1a" />

---

### Task 4: Shared Directory (20 minutes)

1. Create directory: `/opt/dev-project`
2. Set group owner to `developers`
3. Set permissions to `775` (rwxrwxr-x)
4. Test by creating files as `tokyo` and `berlin`

**Verify:** Check permissions and test file creation

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/91ac949a-a736-4ff7-a7f4-82c642fa6e96" />

---

### Task 5: Team Workspace (20 minutes)

1. Create user `nairobi` with home directory
2. Create group `project-team`
3. Add `nairobi` and `tokyo` to `project-team`
4. Create `/opt/team-workspace` directory

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/3a2d770e-d53c-408d-b279-5a8d25578c7b" />

6. Set group to `project-team`, permissions to `775`

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/38702595-aad1-4296-8361-15ba7be151e3" />

8. Test by creating file as `nairobi`

<img width="1040" height="1058" alt="image" src="https://github.com/user-attachments/assets/12a0ebf0-6470-4306-aab2-2cc24f3fd65e" />
