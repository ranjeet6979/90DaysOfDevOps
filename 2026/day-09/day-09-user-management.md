## Challenge Tasks

### Task 1: Create Users (20 minutes)

Create three users with home directories and passwords:
- `tokyo`
- `berlin`
- `professor`
  
<img width="520" height="529" alt="Screenshot 2026-05-31 at 5 43 14 PM" src="https://github.com/user-attachments/assets/82a18636-cb91-48c0-bf82-13311a488c92" />

**Verify:** Check `/etc/passwd` and `/home/` directory

<img width="466" height="95" alt="Screenshot 2026-05-31 at 5 45 03 PM" src="https://github.com/user-attachments/assets/b758f3e8-4b6b-42a0-83cf-45740864ac59" />

<img width="527" height="129" alt="Screenshot 2026-05-31 at 5 45 45 PM" src="https://github.com/user-attachments/assets/532955bc-6c04-4114-bde1-910688a8c391" />

---

### Task 2: Create Groups (10 minutes)

Create two groups:
- `developers`
- `admins`

**Verify:** Check `/etc/group`

<img width="501" height="363" alt="Screenshot 2026-05-31 at 5 46 51 PM" src="https://github.com/user-attachments/assets/d1c2c5c1-18c9-4ded-a2d0-7c6554ec381b" />

---

### Task 3: Assign to Groups (15 minutes)

Assign users:
- `tokyo` → `developers`
- `berlin` → `developers` + `admins` (both groups)
- `professor` → `admins`

<img width="526" height="147" alt="Screenshot 2026-05-31 at 5 47 57 PM" src="https://github.com/user-attachments/assets/20abf87d-8f74-4b99-9abb-4ceffa1878bb" />

**Verify:** Use appropriate command to check group membership

<img width="478" height="111" alt="Screenshot 2026-05-31 at 5 51 18 PM" src="https://github.com/user-attachments/assets/a8260811-d61f-47f6-9a7a-fd8538774ea2" />

---

### Task 4: Shared Directory (20 minutes)

1. Create directory: `/opt/dev-project`
2. Set group owner to `developers`
3. Set permissions to `775` (rwxrwxr-x)
4. Test by creating files as `tokyo` and `berlin`

**Verify:** Check permissions and test file creation

<img width="500" height="696" alt="Screenshot 2026-05-31 at 6 00 25 PM" src="https://github.com/user-attachments/assets/eb7768ed-8ecd-4be7-a455-8fb230b8814f" />

---

### Task 5: Team Workspace (20 minutes)

1. Create user `nairobi` with home directory
2. Create group `project-team`
3. Add `nairobi` and `tokyo` to `project-team`
4. Create `/opt/team-workspace` directory
   
<img width="537" height="277" alt="Screenshot 2026-05-31 at 7 35 41 PM" src="https://github.com/user-attachments/assets/e377d3d4-7ba4-48fe-aad9-224ca8c8022b" />

5. Set group to `project-team`, permissions to `775`
   
<img width="603" height="130" alt="Screenshot 2026-05-31 at 6 26 31 PM" src="https://github.com/user-attachments/assets/e70ec0e6-7ddd-4eb6-b01b-a3dd73bbbfbe" />

6. Test by creating file as `nairobi`
 <img width="525" height="257" alt="Screenshot 2026-05-31 at 6 27 08 PM" src="https://github.com/user-attachments/assets/1144eb74-3508-4753-a29c-f9370871a6c8" />
  
