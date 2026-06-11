# Day 05 – Linux Troubleshooting Drill: CPU, Memory, and Logs

## Task
Today’s goal is to **run a focused troubleshooting drill**.

You will pick a running process/service on your system and:
- Capture a quick health snapshot (CPU, memory, disk, network)
- Trace logs for that service
- Write a **mini runbook** describing what you did and what you’d do next if things were worse

This turns yesterday’s practice into a repeatable troubleshooting routine.

### What’s a runbook?
A **runbook** is a short, repeatable checklist you follow during an incident: the exact commands you run, what you observed, and the next actions if the issue persists. Keep it concise so you can reuse it under pressure.

---

## Expected Output
By the end of today, you should have:

- A markdown file named:  
  `linux-troubleshooting-runbook.md`

or

- A hand written runbook (Recommended)

Your runbook should include both the commands you ran and brief interpretations.

---

## Guidelines
Follow these rules while creating your runbook:

- Run and record output for **at least 8 commands** (save snippets in your runbook)  
  - **Environment basics (2):** `uname -a`, `lsb_release -a` (or `cat /etc/os-release`)
    
    <img width="749" height="339" alt="image" src="https://github.com/user-attachments/assets/0b84fa7b-e06b-4eb1-949e-b130ca22c0f9" />

  - **Filesystem sanity (2):** create a throwaway folder and file, e.g., `mkdir /tmp/runbook-demo`, `cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo`
    
    <img width="677" height="78" alt="image" src="https://github.com/user-attachments/assets/3214f538-46cb-4160-a55a-6c96d50e0ed5" />

  - **CPU / Memory (2):** `top`/`htop`/`ps -o pid,pcpu,pmem,comm -p <pid>`, `free -h`, `vm_stat` (mac)
    
    <img width="711" height="694" alt="image" src="https://github.com/user-attachments/assets/3f783f9a-1d10-4f4f-9be0-bcde33f957d6" />

    <img width="1173" height="689" alt="image" src="https://github.com/user-attachments/assets/6756ae38-d3f3-4914-adb7-f22bc012c491" />

    <img width="366" height="83" alt="image" src="https://github.com/user-attachments/assets/c300eda3-2a70-476e-8e30-ac8c34acfdfe" />

    <img width="431" height="64" alt="image" src="https://github.com/user-attachments/assets/4458562f-5016-4cc2-8b76-16e4f7e2f98d" />



  - **Disk / IO (2):** `df -h`, `du -sh /var/log`, `iostat`/`vmstat`/`dstat`

    <img width="585" height="214" alt="image" src="https://github.com/user-attachments/assets/44f6994b-852f-44da-afb0-8755d60b05cc" />

    <img width="355" height="356" alt="image" src="https://github.com/user-attachments/assets/4cce7a1e-49b5-4c0c-95ec-82f7300184c4" />

    <img width="670" height="172" alt="image" src="https://github.com/user-attachments/assets/08b2c116-d36f-4ebc-87d3-69c460325847" />

    <img width="598" height="64" alt="image" src="https://github.com/user-attachments/assets/92639621-20f1-48cf-b5dd-436ff666dba4" />

    



  - **Network (2):** `ss -tulpn`/`netstat -tulpn`, `curl -I <service-endpoint>`/`ping`  
  - **Logs (2):** `journalctl -u <service> -n 50`, `tail -n 50 /var/log/<file>.log`
- Choose **one target service/process** (e.g., `ssh`, `cron`, `docker`, your web app) and stick to it for the drill.
- For each command, add a 1–2 line note on what you observed (e.g., “CPU spikes to 80% when restarting”, “No recent errors in last 50 lines”).
- End with a **“If this worsens”** section listing 3 next steps you would take (ex: restart strategy, increase log verbosity, collect `strace`).
- Keep it concise and actionable (aim for ~1 page).

Suggested structure for `linux-troubleshooting-runbook.md`:
- Target service / process
- Snapshot: CPU & Memory
- Snapshot: Disk & IO
- Snapshot: Network
- Logs reviewed
- Quick findings
- If this worsens (next steps)

---

## Resources
You may refer to:

- Notes from Day 02–04
- Linux `man` pages (`top`, `ps`, `df`, `journalctl`, `ss/netstat`)
- Your class notes

Avoid generic copy/paste. Use outputs from **your** machine.

---

## Why This Matters for DevOps
Incidents rarely come with perfect clues. A fast, repeatable checklist saves minutes when services misbehave.

This drill builds:
- Habit of capturing evidence before acting
- Confidence reading resource signals (CPU, memory, disk, network)
- Log-first mindset before restarts or escalations

These habits reduce downtime and prevent guesswork in production.

---
