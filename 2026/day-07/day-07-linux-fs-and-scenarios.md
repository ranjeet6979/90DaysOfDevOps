**File System Hierarchy**
Core Directories:

/ (root) - The starting point of everything, contains important directories like home, mnt, etc

/home - User home directories, personalised directory for the user 

/root - Root user's home directory

/etc - Configuration files like sudoes, fstab , ssh, crontab, dhcp

/var/log - Log files e.g auth.log, syslog, 

/tmp - Temporary files

Additional Directories:


/bin - Essential command binaries (link to /usr/bin)

/usr/bin - User command binaries 

/opt - Optional/third-party applications

Hands On task

# Find the largest log file in /var/log

du -sh /var/log/* 2>/dev/null | sort -h | tail -5


<img width="583" height="86" alt="image" src="https://github.com/user-attachments/assets/af95b0b3-ce08-4e54-9129-27f6f662fc62" />

# Look at a config file in /etc

cat /etc/hostname

<img width="367" height="32" alt="image" src="https://github.com/user-attachments/assets/53b3d4d1-e339-4ba5-8869-380534a83820" />

# Check your home directory

ls -la ~

<img width="386" height="145" alt="image" src="https://github.com/user-attachments/assets/1eb24632-93ec-44fa-9065-764acec9cefc" />

**Part 2: Scenario-Based Practice**

Question: How do you check if the 'nginx' service is running?

systemctl status nginx

<img width="910" height="271" alt="image" src="https://github.com/user-attachments/assets/7814a329-4541-4f8d-af16-1cf0fc2c01d2" />

list all servcies: systemctl list-units --type=service

<img width="1049" height="691" alt="image" src="https://github.com/user-attachments/assets/5e9e5e10-69fb-4018-9705-cb758cafc250" />

systemctl is-enabled nginx

<img width="369" height="49" alt="image" src="https://github.com/user-attachments/assets/e995c4f2-f887-4470-a081-2cd9f3296e04" />



============================================================================
**Scenario 1: Service Not Starting**

Step 1: check service running stauts:  systemctl status nginx

<img width="921" height="282" alt="image" src="https://github.com/user-attachments/assets/dd1429a3-4fef-428e-9910-e2965937a3cb" />

Step 2: check nginx logs:  tail -n 40 /var/log/nginx/error.log

<img width="555" height="48" alt="image" src="https://github.com/user-attachments/assets/aa7cd9d9-b414-47dc-aabd-8accea46c138" />

Step 3: check if enabled: systemctl is-enabled nginx

<img width="365" height="35" alt="image" src="https://github.com/user-attachments/assets/69357f5c-f4b3-4607-a9c7-305de876f833" />

Step 4: check journalctl logs 

<img width="918" height="105" alt="image" src="https://github.com/user-attachments/assets/732da6a9-0dd3-4dfe-8b21-69b00aae6e67" />

---

**Scenario 2: High CPU Usage** 
```
Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?
```

**Hint:**
- Use a command that shows **live** CPU usage

<img width="655" height="488" alt="image" src="https://github.com/user-attachments/assets/198b43d6-2a4f-4283-9ce6-d56c46da438e" />

- Look for processes sorted by CPU percentage (shortcut P)

<img width="664" height="493" alt="image" src="https://github.com/user-attachments/assets/de742f67-e44b-4295-9f22-451e7b9a0348" />

- Note the PID (Process ID) of the top process
PID 2707 of highest CPU usage process

- htop output:
<img width="660" height="494" alt="image" src="https://github.com/user-attachments/assets/bd52f83e-ddb6-4c4c-9895-7b74248de2ad" />


**Commands to explore:** `top` (press 'q' to quit), `htop`, `ps aux --sort=-%cpu | head -10`

<img width="934" height="260" alt="image" src="https://github.com/user-attachments/assets/6069c88f-5a20-4267-ad59-daff2326407d" />

**Resource:** Review Day 05 (Troubleshooting Drill - CPU & Memory section)

---


**Scenario 3: Finding Service Logs**

# Check service status first

systemctl status nginx

<img width="912" height="285" alt="image" src="https://github.com/user-attachments/assets/33eafdb6-5d42-4196-aa27-281c3fd7805d" />

# View last 50 lines of logs

journalctl -u nginx -n 50

<img width="909" height="119" alt="image" src="https://github.com/user-attachments/assets/a07e1790-88e7-4431-8cb4-c7a60d7fc636" />

# Follow logs in real-time

journalctl -u nginx -f

<img width="915" height="113" alt="image" src="https://github.com/user-attachments/assets/3070a0a6-b723-407a-a109-1039e16bcca3" />

============================================================================

**Scenario 4: File Permissions Issue**

Step 1: Check current permissions

Command: ls -l /home/user/backup.sh

Look for: -rw-r--r-- (notice no 'x' = not executable)

<img width="348" height="34" alt="image" src="https://github.com/user-attachments/assets/c7bc48f0-d65b-4db1-aadc-6bd544a972ef" />


Step 2: Add execute permission

Command: chmod +x /home/user/backup.sh

Step 3: Verify it worked

Command: ls -l /home/user/backup.sh

Look for: -rwxr-xr-x (notice 'x' = executable)

<img width="356" height="77" alt="image" src="https://github.com/user-attachments/assets/27266b6b-4cd1-4d0a-b9b6-2e55fa320e6b" />


Step 4: Try running it

Command: ./backup.sh

<img width="258" height="46" alt="image" src="https://github.com/user-attachments/assets/702014e2-4f0a-4992-870c-fe61af94ab20" />

**Scenario 4: File Permissions Issue** 
```
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

<img width="315" height="37" alt="image" src="https://github.com/user-attachments/assets/536755b0-1d85-4dcf-a545-5c500641898f" />

What commands would you use to fix this?
```

**Hint:**
- First: Check what permissions the file has
- Understand: Files need 'x' (execute) permission to run
- Fix: Add execute permission with chmod

**Step-by-step solution structure:**

Step 1: Check current permissions
Command: ls -l /home/user/backup.sh

<img width="474" height="111" alt="image" src="https://github.com/user-attachments/assets/76a25e3e-c276-4450-941d-6e8182c2f351" />

Look for: -rw-r--r-- (notice no 'x' = not executable)

Step 2: Add execute permission
Command: chmod +x /home/user/backup.sh

<img width="380" height="23" alt="image" src="https://github.com/user-attachments/assets/13b468de-6f65-4a6b-97dd-b40000e60eb5" />

Step 3: Verify it worked
Command: ls -l /home/user/backup.sh

<img width="452" height="37" alt="image" src="https://github.com/user-attachments/assets/d4cc7be1-43c8-4f0f-a835-abc948f1c174" />

Look for: -rwxr-xr-x (notice 'x' = executable)

Step 4: Try running it
Command: ./backup.sh

<img width="339" height="61" alt="image" src="https://github.com/user-attachments/assets/9d62c21d-80a3-4917-8018-ea528b95debc" />


