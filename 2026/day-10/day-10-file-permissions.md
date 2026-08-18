
### Task 1: Create Files (10 minutes)

1. Create empty file `devops.txt` using `touch`
2. Create `notes.txt` with some content using `cat` or `echo`
3. Create `script.sh` using `vim` with content: `echo "Hello DevOps"`

**Verify:** `ls -l` to see permissions

<br><img width="482" height="332" alt="Screenshot 2026-05-31 at 11 37 39 PM" src="https://github.com/user-attachments/assets/5ba751cc-410d-4494-bbb9-7302d06f4a65" />

### Task 2: Read Files (10 minutes)

<br>1. Read `notes.txt` using `cat`
<br><img width="270" height="40" alt="image" src="https://github.com/user-attachments/assets/1ab6846c-82fc-4f35-a12d-ca789e991dbe" />

<br>2. View `script.sh` in vim read-only mode
<br><img width="671" height="115" alt="image" src="https://github.com/user-attachments/assets/274e2a4b-12c8-40b9-ba1a-639d5bcf5f55" />

<br>3. Display first 5 lines of `/etc/passwd` using `head`
<br><img width="388" height="112" alt="Screenshot 2026-05-31 at 9 00 02 PM" src="https://github.com/user-attachments/assets/1c440db3-13c7-484b-90c3-5a109f463340" />

<br>4. Display last 5 lines of `/etc/passwd` using `tail`
<br><img width="431" height="108" alt="Screenshot 2026-05-31 at 9 01 05 PM" src="https://github.com/user-attachments/assets/b56f43ce-3cec-4a5f-b3e4-bae8567c4947" />

### Task 3: Understand Permissions (10 minutes)

<br>Format: `rwxrwxrwx` (owner-group-others)
<br>- `r` = read (4), `w` = write (2), `x` = execute (1)

<br>Check your files: `ls -l devops.txt notes.txt script.sh`
<br><img width="460" height="100" alt="image" src="https://github.com/user-attachments/assets/a6cf5dce-2d4a-4f1e-ac76-25960ef545df" />

<br>Q: What are current permissions? Who can read/write/execute?
<br>A: Current permissions are read write for user ranjeet, read write for group ranjeet and only read for others.

### Task 4: Modify Permissions (20 minutes)

<br>1. Make `script.sh` executable → run it with `./script.sh`
<br><img width="310" height="59" alt="image" src="https://github.com/user-attachments/assets/84ff56c2-89ab-490c-9b48-c96ad588dba3" />
  
<br>2. Set `devops.txt` to read-only (remove write for all)
<br><img width="448" height="100" alt="image" src="https://github.com/user-attachments/assets/0fb4b54c-18c8-499d-b079-620c5697d2ef" />

<br>3. Set `notes.txt` to `640` (owner: rw, group: r, others: none)
<br><img width="461" height="100" alt="image" src="https://github.com/user-attachments/assets/fddfc689-278f-4b72-b739-eb07cf27b8fb" />

<br>4. Create directory `project/` with permissions `755`
<br><img width="450" height="96" alt="image" src="https://github.com/user-attachments/assets/0b5b97d0-a47b-4fb1-9206-2cfba781f5b5" />

**Verify:** `ls -l` after each change

### Task 5: Test Permissions (10 minutes)

<br>1. Try writing to a read-only file - what happens?
<br>shows message E45: read only option is set (add ! to override) 
<br><img width="422" height="764" alt="image" src="https://github.com/user-attachments/assets/e0f0ebc1-3f64-4b5c-b56a-89fd2fe082b7" />

<br>2. Try executing a file without execute permission
<br>shows error Permission denied
<br><img width="468" height="95" alt="image" src="https://github.com/user-attachments/assets/c1d41e65-c0b8-4a9d-8a31-faa474ed0f58" />
