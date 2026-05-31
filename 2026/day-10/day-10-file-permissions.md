### Task 1: Create Files (10 minutes)

1. Create empty file `devops.txt` using `touch`
2. Create `notes.txt` with some content using `cat` or `echo`
3. Create `script.sh` using `vim` with content: `echo "Hello DevOps"`

**Verify:** `ls -l` to see permissions

<img width="595" height="220" alt="Screenshot 2026-05-31 at 7 59 14 PM" src="https://github.com/user-attachments/assets/efde2df6-86e0-4aa9-ba73-6a03b65d86ca" />

---

### Task 2: Read Files (10 minutes)

1. Read `notes.txt` using `cat`
   
   <img width="304" height="38" alt="Screenshot 2026-05-31 at 8 13 24 PM" src="https://github.com/user-attachments/assets/fded971d-386e-408d-9433-a63c5d068917" />

2. View `script.sh` in vim read-only mode

<img width="216" height="133" alt="Screenshot 2026-05-31 at 8 15 39 PM" src="https://github.com/user-attachments/assets/bf26c6ba-ca04-41aa-8a02-b682b9782269" />

   
4. Display first 5 lines of `/etc/passwd` using `head`

<img width="388" height="112" alt="Screenshot 2026-05-31 at 9 00 02 PM" src="https://github.com/user-attachments/assets/1c440db3-13c7-484b-90c3-5a109f463340" />
  
6. Display last 5 lines of `/etc/passwd` using `tail`

<img width="431" height="108" alt="Screenshot 2026-05-31 at 9 01 05 PM" src="https://github.com/user-attachments/assets/b56f43ce-3cec-4a5f-b3e4-bae8567c4947" />

---

### Task 3: Unders
tand Permissions (10 minutes)

Format: `rwxrwxrwx` (owner-group-others)
- `r` = read (4), `w` = write (2), `x` = execute (1)

Check your files: `ls -l devops.txt notes.txt script.sh`

<img width="427" height="81" alt="Screenshot 2026-05-31 at 9 01 53 PM" src="https://github.com/user-attachments/assets/ecec8ff8-ba38-44a1-b61e-bb87a42a0a6a" />

Answer: What are current permissions? Who can read/write/execute?

---

### Task 4: Modify Permissions (20 minutes)

1. Make `script.sh` executable → run it with `./script.sh`

<img width="291" height="77" alt="Screenshot 2026-05-31 at 9 03 01 PM" src="https://github.com/user-attachments/assets/e11d3614-1563-454e-ab91-f5a43226a166" />
  
3. Set `devops.txt` to read-only (remove write for all)

<img width="398" height="64" alt="Screenshot 2026-05-31 at 9 04 28 PM" src="https://github.com/user-attachments/assets/d7a52be5-006c-4ffb-88b7-cd6ae22ef76f" />

4. Set `notes.txt` to `640` (owner: rw, group: r, others: none)

<img width="408" height="93" alt="Screenshot 2026-05-31 at 9 05 33 PM" src="https://github.com/user-attachments/assets/8e94ee35-3b26-42a9-bb27-3b622dd545fd" />

5. Create directory `project/` with permissions `755`

<img width="406" height="115" alt="Screenshot 2026-05-31 at 9 07 02 PM" src="https://github.com/user-attachments/assets/d44521c5-1397-4fbd-a1be-3076cff17027" />

**Verify:** `ls -l` after each change

---

### Task 5: Test Permissions (10 minutes)

1. Try writing to a read-only file - what happens?
2. Try executing a file without execute permission
3. Document the error messages
