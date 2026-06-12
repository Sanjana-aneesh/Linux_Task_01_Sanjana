# Linux Task 01 — Command Outputs

**Submitted by:** Sanjana
**Date:** 12 June 2026

---

## Part B — Basic Navigation Commands

### 1. pwd
**Purpose:** Displays the full path of the current working directory.
**Output:**
```
/home/kali
```

### 2. ls
**Purpose:** Lists all visible files and folders in the current directory.
**Output:**
```
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```

### 3. ls -la
**Purpose:** Lists all files and folders including hidden ones with detailed info like permissions, owner, size and date.
**Output:**
```
total 164
drwx------ 16 kali kali  4096 Jun 12 00:42 .
drwxr-xr-x  3 root root  4096 Mar 20 02:45 ..
-rw-r--r--  1 kali kali   220 Mar 20 02:45 .bash_logout
-rw-r--r--  1 kali kali  5578 Mar 20 02:45 .bashrc
drwxr-xr-x  2 kali kali  4096 Jun 12 00:35 Desktop
drwxr-xr-x  2 kali kali  4096 Jun 12 00:35 Documents
drwxr-xr-x  2 kali kali  4096 Jun 12 00:35 Downloads
...
```

### 4. cd
**Purpose:** Navigates into a different directory.
**Command:** `cd Desktop`
**Output:** Prompt changes to `(kali@kali)-[~/Desktop]`

### 5. clear
**Purpose:** Clears the terminal screen. Previously run commands are still accessible by scrolling up.
**Output:** Terminal screen becomes empty.

### 6. history
**Purpose:** Shows a numbered list of all previously run commands.
**Output:**
```
1  uname -a
2  pwd
3  ls
4  ls -la
5  cd Desktop
6  whoami
7  hostname
8  history
```

### 7. whoami
**Purpose:** Displays the currently logged in username.
**Output:**
```
kali
```

### 8. hostname
**Purpose:** Displays the name of the machine on the network.
**Output:**
```
kali
```

---

## Part C — Directory Management

### Commands Used
```
mkdir CyberSecurity_Lab
cd CyberSecurity_Lab
mkdir Networking
mkdir Linux
mkdir CyberSecurity
mkdir EthicalHacking
mkdir Reports
tree
```
**Output of tree:**
```
.
├── CyberSecurity
├── EthicalHacking
├── Linux
├── Networking
└── Reports

6 directories, 0 files
```

---

## Part D — File Management

### touch — Create files
**Purpose:** Creates new empty files.
```
touch notes.txt commands.txt report.txt
```
**Output of ls:**
```
commands.txt  CyberSecurity  EthicalHacking  Linux  Networking  notes.txt  Reports  report.txt
```

### cp — Copy files
**Purpose:** Copies a file to another location. Original stays in place.
```
cp notes.txt Networking/
ls Networking/
```
**Output:**
```
notes.txt
```

### mv — Move files
**Purpose:** Moves a file to a different location.
```
mv commands.txt Linux/
ls Linux/
```
**Output:**
```
commands.txt
```

### mv — Rename files
**Purpose:** Renames a file.
```
mv report.txt renamed_report.txt
ls
```
**Output:**
```
CyberSecurity  EthicalHacking  Linux  Networking  notes.txt  renamed_report.txt  Reports
```

### rm — Delete files
**Purpose:** Permanently deletes a file.
```
rm renamed_report.txt
ls
```
**Output:**
```
CyberSecurity  EthicalHacking  Linux  Networking  notes.txt  Reports
```

---

## Part E — System Information

### Commands and Outputs

```
$ uname -a
Linux kali 6.18.12+kali-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.18.12-1kali1 (2026-02-25) x86_64 GNU/Linux

$ hostname
kali

$ whoami
kali

$ date
Fri Jun 12 01:04:49 AM EDT 2026

$ uptime
01:04:56 up 29 min,  1 user,  load average: 0.26, 0.41, 0.35

$ pwd
/home/kali/CyberSecurity_Lab
```
