# Commands Used — Linux Task 02

**Submitted by:** Sanjana
**Date:** 12 June 2026

---

## Part A — Understanding Users

### whoami
**Purpose:** Displays the currently logged in username.
**Output:**
```
kali
```

### id
**Purpose:** Shows the user's UID, GID and all groups they belong to.
**Output:**
```
uid=1000(kali) gid=1000(kali) groups=1000(kali),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),101(netdev),102(scanner),104(bluetooth),113(lpadmin),122(wireshark),123(kaboxer),124(vboxsf)
```

### cat /etc/passwd
**Purpose:** Displays all user accounts on the system including system users.
**Format of each line:** `username:password:UID:GID:info:home_dir:shell`
**Example:**
```
root:x:0:0:root:/root:/usr/bin/zsh
kali:x:1000:1000::/home/kali:/usr/bin/zsh
```

### Answers to Part A Questions

**1. What is your current username?**
`kali`

**2. What is UID?**
UID stands for User ID. It is a unique number assigned to every user on a Linux system. My UID is `1000`. The root user always has UID `0`.

**3. What is GID?**
GID stands for Group ID. It is a unique number assigned to a group. My GID is `1000` which corresponds to the `kali` group.

**4. What information does /etc/passwd contain?**
The `/etc/passwd` file contains information about every user account on the system. Each line has 7 fields separated by colons: username, password placeholder (x), UID, GID, user description, home directory, and default shell. It includes both real users and system service accounts.

---

## Part B — Create Users & Groups

### Create Groups
```
sudo groupadd interns
sudo groupadd cyberteam
```

### Create Users
```
sudo useradd student1
sudo useradd student2
sudo useradd student3
```

### Add Users to Groups
```
sudo usermod -aG interns student1
sudo usermod -aG interns student2
sudo usermod -aG cyberteam student3
```

### Verify
```
groups student1
groups student2
id student1
id student2
```

**Output:**
```
student1 : student1 interns
student2 : student2 interns
uid=1001(student1) gid=1003(student1) groups=1003(student1),1001(interns)
uid=1002(student2) gid=1004(student2) groups=1004(student2),1001(interns)
```

---

## Part C — File Ownership

### Create folder and files
```
mkdir ~/CyberSecurity_Project
cd ~/CyberSecurity_Project
touch report.txt notes.txt credentials.txt
ls -l
```

**Output (before chown):**
```
-rw-rw-r-- 1 kali  kali 0 Jun 12 02:39 credentials.txt
-rw-rw-r-- 1 kali  kali 0 Jun 12 02:39 notes.txt
-rw-rw-r-- 1 kali  kali 0 Jun 12 02:39 report.txt
```

### Change Ownership
```
sudo chown student1 report.txt
ls -l
```

**Output (after chown):**
```
-rw-rw-r-- 1 kali     kali 0 Jun 12 02:39 credentials.txt
-rw-rw-r-- 1 kali     kali 0 Jun 12 02:39 notes.txt
-rw-rw-r-- 1 student1 kali 0 Jun 12 02:39 report.txt
```

**Documentation:**
| Field | Value |
|-------|-------|
| Original Owner | `kali` |
| New Owner | `student1` |
| Command Used | `sudo chown student1 report.txt` |

---

## Part D — File Permissions

### Create file and check default permissions
```
touch security_policy.txt
ls -l security_policy.txt
```
**Output:** `-rw-rw-r-- 1 kali kali 0 Jun 12 02:49 security_policy.txt`

### Read Only (r--r--r--)
```
chmod 444 security_policy.txt
ls -l security_policy.txt
```
**Output:** `-r--r--r-- 1 kali kali 0 Jun 12 02:49 security_policy.txt`

### Read & Write (rw-rw-r--)
```
chmod 664 security_policy.txt
ls -l security_policy.txt
```
**Output:** `-rw-rw-r-- 1 kali kali 0 Jun 12 02:49 security_policy.txt`

### Full Access (rwxrwxrwx)
```
chmod 777 security_policy.txt
ls -l security_policy.txt
```
**Output:** `-rwxrwxrwx 1 kali kali 0 Jun 12 02:49 security_policy.txt`
