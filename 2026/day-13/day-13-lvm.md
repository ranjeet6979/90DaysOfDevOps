# Day 13 – Linux Volume Management (LVM)

## Task
Learn LVM to manage storage flexibly – create, extend, and mount volumes.

**Watch First:** [Linux LVM Tutorial](https://youtu.be/Evnf2AAt7FQ?si=ncnfQYySYtK_2K3c)

---

## Expected Output
- A markdown file: `day-13-lvm.md`
- Screenshots of command outputs

---

## Before You Start

Switch to root user:
```bash
sudo -i
```
or
```bash
sudo su
```
No spare disk? Create a virtual one (watch the tutorial):
```bash
dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024
losetup -fP /tmp/disk1.img
losetup -a   # Note the device name (e.g., /dev/loop0)
```

---

## Challenge Tasks

### Task 1: Check Current Storage
Run: `lsblk`, `pvs`, `vgs`, `lvs`, `df -h`

<img width="471" height="160" alt="image" src="https://github.com/user-attachments/assets/fc3df98c-569a-4063-b2d5-39cc8ef34130" />

<img width="590" height="271" alt="image" src="https://github.com/user-attachments/assets/d0e74413-2ccd-4039-956c-06a4510548dc" />

**lsblk output after attaching device:**

lsblk -o +SERIAL
<img width="618" height="159" alt="image" src="https://github.com/user-attachments/assets/0986e5ac-63b5-4936-8702-83307ebef3fb" />

lsblk -o NAME,SIZE,TYPE,MOUNTPOINT,SERIAL

<img width="546" height="157" alt="image" src="https://github.com/user-attachments/assets/162e7781-0612-419c-8cfb-2db62a7a9b1d" />


### Task 2: Create Physical Volume
```bash
pvcreate /dev/sdb   # or your loop device
pvs

<img width="406" height="89" alt="image" src="https://github.com/user-attachments/assets/20d2069b-3c0f-4830-b630-a786ad1216a4" />

```

### Task 3: Create Volume Group
```bash
vgcreate devops-vg /dev/sdb
vgs

<img width="477" height="120" alt="image" src="https://github.com/user-attachments/assets/ae17bd4b-2648-499a-bfea-854c1099ff31" />

```

### Task 4: Create Logical Volume
```bash
lvcreate -L 500M -n app-data devops-vg
lvs

<img width="643" height="87" alt="image" src="https://github.com/user-attachments/assets/6c042443-ebfc-41cf-80d4-bf71d4e35af4" />

pvdisplay and vgdisplay output

<img width="447" height="478" alt="image" src="https://github.com/user-attachments/assets/108e9b0b-9555-4dd9-8b23-28eac223c6fd" />

<img width="538" height="408" alt="image" src="https://github.com/user-attachments/assets/e242d3c8-477a-4d8a-92ac-b4c18fcecdf4" />

```

### Task 5: Format and Mount
```bash
mkfs.ext4 /dev/devops-vg/app-data
mkdir -p /mnt/app-data
mount /dev/devops-vg/app-data /mnt/app-data
df -h /mnt/app-data

<img width="700" height="591" alt="image" src="https://github.com/user-attachments/assets/e166bb52-e2da-490c-85f1-a1321d913065" />

<img width="645" height="47" alt="image" src="https://github.com/user-attachments/assets/5f24c534-1245-4d70-a5d0-b6b23b4320d9" />

```

### Task 6: Extend the Volume
```bash
lvextend -L +200M /dev/devops-vg/app-data

<img width="771" height="88" alt="image" src="https://github.com/user-attachments/assets/6d5dad60-e48b-4672-82c3-467db44b9028" />

df -h will still display old size for mount, hence need to run resize2fs
resize2fs /dev/devops-vg/app-data

df -h /mnt/app-data

<img width="716" height="310" alt="image" src="https://github.com/user-attachments/assets/e2f1975e-1b79-4730-a6a4-27098a8e8550" />


```

---

## Documentation

Create `day-13-lvm.md` with:
- Commands used
- Screenshots of outputs
- What you learned (3 points)

---
Happy Learning!
**TrainWithShubham**
