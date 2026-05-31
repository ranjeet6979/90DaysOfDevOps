
### Task 1: Create Files (10 minutes)

1. Create empty file `devops.txt` using `touch`
2. Create `notes.txt` with some content using `cat` or `echo`
3. Create `script.sh` using `vim` with content: `echo "Hello DevOps"`

**Verify:** `ls -l` to see permissions

<img width="482" height="332" alt="Screenshot 2026-05-31 at 11 37 39 PM" src="https://github.com/user-attachments/assets/5ba751cc-410d-4494-bbb9-7302d06f4a65" />
---

### Task 2: Read Files (10 minutes)

1. Read `notes.txt` using `cat`
   
<img width="270" height="40" alt="image" src="https://github.com/user-attachments/assets/1ab6846c-82fc-4f35-a12d-ca789e991dbe" />

2. View `script.sh` in vim read-only mode

<img width="671" height="115" alt="image" src="https://github.com/user-attachments/assets/274e2a4b-12c8-40b9-ba1a-639d5bcf5f55" />

4. Display first 5 lines of `/etc/passwd` using `head`

<img width="388" height="112" alt="Screenshot 2026-05-31 at 9 00 02 PM" src="https://github.com/user-attachments/assets/1c440db3-13c7-484b-90c3-5a109f463340" />
  
6. Display last 5 lines of `/etc/passwd` using `tail`

<img width="431" height="108" alt="Screenshot 2026-05-31 at 9 01 05 PM" src="https://github.com/user-attachments/assets/b56f43ce-3cec-4a5f-b3e4-bae8567c4947" />

---

### Task 3: Understand Permissions (10 minutes)

Format: `rwxrwxrwx` (owner-group-others)
- `r` = read (4), `w` = write (2), `x` = execute (1)

Check your files: `ls -l devops.txt notes.txt script.sh`

<img width="460" height="100" alt="image" src="https://github.com/user-attachments/assets/a6cf5dce-2d4a-4f1e-ac76-25960ef545df" />

Answer: What are current permissions? Who can read/write/execute?
Current permissions are read write for user ranjeet, read write for group ranjeet and only read for others.
---

### Task 4: Modify Permissions (20 minutes)

1. Make `script.sh` executable → run it with `./script.sh`

<img width="310" height="59" alt="image" src="https://github.com/user-attachments/assets/84ff56c2-89ab-490c-9b48-c96ad588dba3" />
  
3. Set `devops.txt` to read-only (remove write for all)

<img width="448" height="100" alt="image" src="https://github.com/user-attachments/assets/0fb4b54c-18c8-499d-b079-620c5697d2ef" />

4. Set `notes.txt` to `640` (owner: rw, group: r, others: none)

<img width="461" height="100" alt="image" src="https://github.com/user-attachments/assets/fddfc689-278f-4b72-b739-eb07cf27b8fb" />

5. Create directory `project/` with permissions `755`

<img width="450" height="96" alt="image" src="https://github.com/user-attachments/assets/0b5b97d0-a47b-4fb1-9206-2cfba781f5b5" />

**Verify:** `ls -l` after each change

---

### Task 5: Test Permissions (10 minutes)

1. Try writing to a read-only file - what happens?

shows message E45: read only option is set (add ! to override) 

<img width="422" height="764" alt="image" src="https://github.com/user-attachments/assets/e0f0ebc1-3f64-4b5c-b56a-89fd2fe082b7" />

2. Try executing a file without execute permission
shows error Permission denied

<img width="468" height="95" alt="image" src="https://github.com/user-attachments/assets/c1d41e65-c0b8-4a9d-8a31-faa474ed0f58" />
