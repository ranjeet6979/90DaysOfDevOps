# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Task
Today's goal is to **deploy a real web server on the cloud** and learn practical server management.

You will:
- Launch a cloud instance (AWS EC2 or Utho)
- Connect via SSH
- Install Nginx
- Configure security groups for web access (port 80 by default for nginx)
- Extract and save logs to a file
- Verify your webpage is accessible from the internet

This is real DevOps work - exactly what you'll do in production.

---

## Expected Output
By the end of today, you should have:

1. A markdown file named: `day-08-cloud-deployment.md`
2. Screenshots showing:
   - SSH connection to your server
   - Nginx welcome page accessible from browser
   - Log file contents
3. The log file: `nginx-logs.txt`

---

## Prerequisites
- AWS account (Free Tier) OR Utho account
- Basic understanding of Linux commands (Days 1-7)
- SSH client (Terminal on Mac/Linux, PuTTY on Windows)

---

## Guidelines

### Part 1: Launch Cloud Instance & SSH Access (15 minutes)

**Step 1: Create a Cloud Instance**

<img width="1156" height="479" alt="image" src="https://github.com/user-attachments/assets/74397a11-ce46-450f-a45a-f5867719eb38" />

**Step 2: Connect via SSH**

<img width="847" height="635" alt="image" src="https://github.com/user-attachments/assets/4a271373-c3ac-4a03-b83f-ea36d0910f78" />

---

### Part 2: Install Docker & Nginx (20 minutes)

**Step 1: Update System**

<img width="1342" height="292" alt="image" src="https://github.com/user-attachments/assets/684131f2-cd1e-4af2-bc9d-7a1bee373c33" />

**Step 3: Install Nginx**

<img width="1332" height="691" alt="image" src="https://github.com/user-attachments/assets/7b6568f8-100f-443a-baa2-731a522f1279" />


**Verify Nginx is running:**

<img width="1030" height="295" alt="image" src="https://github.com/user-attachments/assets/5812e38e-c89e-45f6-be78-967159bcf153" />

---

### Part 3: Security Group Configuration (10 minutes)

**Test Web Access:**
Open browser and visit: `http://<your-instance-ip>`

You should see the **Nginx welcome page**!

📸 **Screenshot this page** - you'll need it for submission

<img width="955" height="262" alt="image" src="https://github.com/user-attachments/assets/bccc7206-c6da-4089-ac84-c445f11f2a0e" />

---

### Part 4: Extract Nginx Logs (15 minutes)

**Step 1: View Nginx Logs**
access.log

<img width="1343" height="210" alt="image" src="https://github.com/user-attachments/assets/fd1d10f2-177f-45a2-9221-b2783c2257c9" />

**Step 2: Save Logs to File**

<img width="585" height="53" alt="image" src="https://github.com/user-attachments/assets/7bf75d01-1afa-4ba4-b81e-51d6f33b6ce7" />

**Step 3: Download Log File to Your Local Machine**
```bash
# On your local machine (new terminal window)
# For AWS:
scp -i your-key.pem ubuntu@<your-instance-ip>:~/nginx-logs.txt .

<img width="935" height="137" alt="image" src="https://github.com/user-attachments/assets/953a17c7-16a1-447b-8939-ae33ca689ef5" />

# For Utho:
scp root@<your-instance-ip>:~/nginx-logs.txt .
```

---


## Documentation Template

Create your `day-08-cloud-deployment.md` with this structure:

## Commands Used
scp -i key.pem dest_user@dest_ip:/dest_path local path
ssh -i key.pem dest_user@dest_ip

## Challenges Faced
No

## What I Learned


---


## Why This Matters for DevOps

This exercise teaches you:
- **Cloud infrastructure provisioning** - launching and configuring servers
- **Remote server management** - SSH, security, access control
- **Service deployment** - installing and running applications
- **Log management** - accessing and analyzing logs
- **Security** - configuring firewalls and security groups

These are core skills for any DevOps engineer working in production.

---


## Submission
1. Fork this `90DaysOfDevOps` repository
2. Navigate to the `2026/day-08/` folder
3. Add your `day-08-cloud-deployment.md` file
4. Add your `nginx-logs.txt` file
5. Add screenshots (name them: `ssh-connection.png`, `nginx-webpage.png`, `docker-nginx.png`)
6. Commit and push your changes to your fork

---
