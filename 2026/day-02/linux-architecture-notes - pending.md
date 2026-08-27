# Linux Fundamentals

---

# Explain Process States (Running, Sleeping, Zombie, etc.)

## Simple Trick to Remember

**RSDTZO**

```text
R = Running
S = Sleeping
D = Don't Disturb (Uninterruptible Sleep)
T = Temporarily Stopped
Z = Zombie
O = Orphan
```

---

## 1. Running (R) 🏃

- The process is currently executing on the CPU or waiting for CPU time.
- Example: A script, command, or application actively running.

**Memory Trick:**

> R = Running Race

---

## 2. Sleeping (S) 😴

- The process is waiting for an event such as keyboard input, disk response, or network data.
- Most Linux processes spend most of their time in this state.

**Memory Trick:**

> S = Sleeping and can be awakened easily.

---

## 3. Uninterruptible Sleep (D) 🚧

- The process is waiting for a critical I/O operation such as disk or storage access.
- It cannot be interrupted until the operation completes.

**Memory Trick:**

> D = Don't Disturb

**Examples:**
- Stuck disk read/write operation
- Waiting on NFS storage
- Storage latency issues

---

## 4. Stopped (T) ✋

- The process execution has been paused.
- Usually caused by signals such as `Ctrl + Z`.

**Memory Trick:**

> T = Temporarily Stopped

**Example:**

```bash
vi file.txt
# Press Ctrl + Z
```

---

## 5. Zombie (Z) 🧟

- The process has completed execution.
- Its parent process has not yet collected its exit status.
- The process remains visible in the process table.

**Memory Trick:**

> Z = Zombie is dead but still visible.

---

## 6. Orphan Process (O) 👶

- The parent process terminates before the child process.
- `systemd` (PID 1) adopts the child process.

**Memory Trick:**

> O = Orphan child without a parent.

---

## Office Analogy

```text
Running  -> Employee is working
Sleeping -> Waiting for an email/task
D State  -> Waiting for a slow server or disk
Stopped  -> Manager said Pause
Zombie   -> Employee left but HR record exists
Orphan   -> Manager left, new manager assigned
```

### One-Line Interview Answer

> A Linux process can be in Running (R), Sleeping (S), Uninterruptible Sleep (D), Stopped (T), or Zombie (Z) state. Running means executing, Sleeping means waiting for an event, D means waiting for I/O, Stopped means paused, and Zombie means completed but not yet cleaned up by its parent process.

---

# List 5 Commands You Would Use Daily

- `ls` – Lists files and directories in the current location.
- `cat` – Displays the contents of a file on the terminal.
- `mv` – Moves or renames files and directories.
- `cp` – Copies files or directories from one location to another.
- `less` – Views file contents one page at a time with scrolling support.
- `head` – Displays the first few lines of a file (default: 10 lines).
- `tail` – Displays the last few lines of a file and can monitor updates in real time.
- `vi` – Opens the Vi/Vim text editor to create or edit files.

---

# Linux Boot Process

## Simplified Version

1. Power On the system.
2. BIOS/UEFI performs hardware checks and loads the bootloader.
3. Bootloader (GRUB) loads the Linux kernel.
4. Kernel initializes hardware and mounts the filesystem.
5. Kernel starts `systemd` (PID 1).
6. `systemd` starts services like NetworkManager, SSH, Docker, and Kubernetes.
7. User gets the login prompt or GUI.

---

## Detailed Linux Boot Process

### 1. Power On

- The system receives power and the CPU begins executing firmware instructions.

### 2. BIOS/UEFI Initialization

- BIOS/UEFI performs POST (Power-On Self-Test) to verify hardware such as CPU, RAM, and storage.
- It then identifies a bootable device.

### 3. Bootloader Execution

- BIOS loads the bootloader from the MBR.
- UEFI loads the bootloader from the EFI System Partition (ESP).
- GRUB is the most commonly used Linux bootloader.

### 4. Kernel Loading

- The bootloader loads the Linux kernel and initramfs/initrd into memory.
- Control is then transferred to the kernel.

### 5. Kernel Initialization

- The kernel initializes CPU, memory, device drivers, filesystems, and hardware components.
- It mounts the temporary root filesystem (initramfs).

### 6. Root Filesystem Mount

- The kernel mounts the actual root filesystem (`/`).

### 7. Start Init/Systemd

- The kernel starts `systemd` (or another init system) as PID 1.
- This is the first user-space process.

### 8. Service Startup

- `systemd` starts required services and daemons such as:
  - NetworkManager
  - sshd
  - Docker
  - kubelet
  - Logging services

### 9. Reach Target/Runlevel

- The system reaches the configured target:
  - Multi-user mode (CLI)
  - Graphical mode (GUI)

### 10. User Login

- A login prompt or desktop environment is presented to the user.

---

## Boot Flow Diagram

```text
Power On
   ↓
BIOS/UEFI
   ↓
POST
   ↓
Bootloader (GRUB)
   ↓
Kernel + initramfs
   ↓
Root Filesystem Mount
   ↓
systemd (PID 1)
   ↓
Services Started
   ↓
Login Prompt / GUI
```

---

## One-Line Explanation

- **Power On** → Hardware gets electricity.
- **BIOS/UEFI** → Checks hardware and finds a bootable device.
- **Kernel** → Linux kernel is loaded into memory.
- **Systemd** → Kernel starts PID 1 (`systemd`).
- **Services** → `systemd` starts network, SSH, Docker, kubelet, etc.
- **Login** → User gets a CLI or GUI login screen.

---

## Interview Answer

> When the system is powered on, BIOS/UEFI performs POST and loads the bootloader (GRUB). GRUB loads the Linux kernel and initramfs. The kernel initializes hardware and mounts the root filesystem. It then starts systemd as PID 1, which launches system services and finally presents the login prompt or GUI.

---

## Easy Trick to Remember

### PBKSSL

```text
P = Power
B = BIOS/UEFI
K = Kernel
S = Systemd
S = Services
L = Login
```

### Flow

```text
Power On
   ↓
BIOS/UEFI
   ↓
Kernel
   ↓
Systemd (PID 1)
   ↓
Services
   ↓
Login
```

### Memory Sentence

> **Power Brings Kernel Services to Life**
``
