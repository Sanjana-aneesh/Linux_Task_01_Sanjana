# Linux Task 02 — Users, Groups & File Permissions

**Intern:** Sanjana
**Date:** 12 June 2026
**Organization:** White Band Associates
**OS:** Kali Linux 2026.1 on Oracle VirtualBox

---

## 📁 Repository Structure

| File/Folder | Description |
|-------------|-------------|
| `Screenshots/` | All screenshots for Part A, B, C & D |
| `Commands_Used/commands_used.md` | All commands with outputs and answers |
| `Permission_Analysis/permission_analysis.md` | Part E — Permission analysis |
| `Security_Challenge/security_challenge.md` | Part F — Security challenge answers |
| `Research_Answers/research_answers.md` | Part G — Research answers |

---

## 📋 Summary of Findings

### 👤 Part A — Understanding Users
Ran `whoami`, `id` and `cat /etc/passwd`. Current user is `kali` with UID `1000` and GID `1000`. The `id` command showed the user belongs to many groups including `sudo` and `wireshark`. The `/etc/passwd` file stores every user account on the system with their UID, GID, home directory and default shell.

### 👥 Part B — Create Users & Groups
Created two groups — `interns` and `cyberteam` — using `groupadd`. Created three users — `student1`, `student2`, `student3` — using `useradd`. Added `student1` and `student2` to `interns` and `student3` to `cyberteam` using `usermod -aG`. Verified with `groups` and `id` commands.

### 📁 Part C — File Ownership
Created `CyberSecurity_Project` folder with `report.txt`, `notes.txt` and `credentials.txt`. All files were originally owned by `kali`. Used `sudo chown student1 report.txt` to change ownership of `report.txt` to `student1`. Confirmed with `ls -l`.

### 🔒 Part D — File Permissions
Created `security_policy.txt` and applied three permission levels using `chmod`:
- `chmod 444` → `-r--r--r--` (Read Only — no one can modify)
- `chmod 664` → `-rw-rw-r--` (Read & Write — owner and group can edit)
- `chmod 777` → `-rwxrwxrwx` (Full Access — everyone has complete access)

### 🔢 Part E — Permission Analysis
Analysed 5 numeric permissions with owner, group and other rights explained along with real world use cases. `755` for executables, `644` for regular files, `777` is dangerous and should be avoided, `600` for sensitive private files, `700` for private scripts.

### 🛡️ Part F — Security Challenge
As a Linux Administrator, recommended permissions for 4 files — `600` for `password_backup.txt` and `personal_notes.txt`, `644` for `public_notice.txt` and `640` for `system_log.txt` — with reasoning for each decision.

### 🔬 Part G — Linux Security Research
File permissions are the foundation of Linux security. Giving sensitive files `777` is extremely dangerous as it allows anyone to read, modify or execute them. The Principle of Least Privilege means giving users only the minimum access they need. Organisations restrict access to protect sensitive data, prevent insider threats and meet legal compliance requirements.
