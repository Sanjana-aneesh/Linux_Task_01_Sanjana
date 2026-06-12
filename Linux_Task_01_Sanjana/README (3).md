# Linux Task 01 — Linux Environment Setup & Essential Commands

**Intern:** Sanjana
**Date:** 12 June 2026
**Organization:** White Band Associates
**OS:** Kali Linux 2026.1 on Oracle VirtualBox

---

## 📁 Repository Structure

| File/Folder | Description |
|-------------|-------------|
| `Screenshots/` | Part A, B, C, D & E — All command screenshots |
| `Command_Outputs/command_outputs.md` | Part B, C, D & E — All command outputs with purposes |
| `Answers.md` | Part F — Linux research answers |
| `Notes.md` | Personal notes and observations from the task |
| `README.md` | Summary of all parts |

---

## 📋 Summary of Findings

### 🖥️ Part A — Linux Installation
Successfully installed **Kali Linux 2026.1** on Oracle VirtualBox. Kali Linux was chosen because it is specifically designed for cybersecurity and ethical hacking, making it the most relevant choice for this internship. Screenshots of the desktop environment, terminal window and system information using `uname -a` are included in the Screenshots folder.

### 🧭 Part B — Basic Navigation Commands
Practised 8 essential Linux terminal commands:
- `pwd` — showed current directory as `/home/kali`
- `ls` — listed all visible folders like Desktop, Downloads, Documents
- `ls -la` — listed all files including hidden ones with permissions and sizes
- `cd Desktop` — navigated into the Desktop folder
- `clear` — cleared the terminal screen
- `history` — listed all previously run commands with line numbers
- `whoami` — returned `kali` as the current user
- `hostname` — returned `kali` as the machine name

### 📁 Part C — Directory Management
Created the `CyberSecurity_Lab` folder with 5 subfolders — `Networking`, `Linux`, `CyberSecurity`, `EthicalHacking` and `Reports` — using `mkdir` for each folder. Used `cd` to navigate inside and `tree` to display the complete folder structure visually. Tree output confirmed `6 directories, 0 files`.

### 📄 Part D — File Management
Performed all 5 file operations inside `CyberSecurity_Lab`:
- **Created** `notes.txt`, `commands.txt`, `report.txt` using `touch`
- **Copied** `notes.txt` to `Networking/` using `cp`
- **Moved** `commands.txt` to `Linux/` using `mv`
- **Renamed** `report.txt` to `renamed_report.txt` using `mv`
- **Deleted** `renamed_report.txt` using `rm`

### ⚙️ Part E — System Information Collection
Ran 6 system commands and recorded:
- **Kernel Version:** `Linux kali 6.18.12+kali-amd64 x86_64 GNU/Linux`
- **Username:** `kali`
- **Hostname:** `kali`
- **Current Directory:** `/home/kali/CyberSecurity_Lab`
- **Date & Time:** `Fri Jun 12 01:04:49 AM EDT 2026`
- **System Uptime:** `29 minutes, 1 user, load average: 0.26, 0.41, 0.35`

### 🔬 Part F — Linux Research
Researched and explained 5 key topics:
- **What is Linux** — free and open source OS created by Linus Torvalds in 1991
- **Linux in Cybersecurity** — powers most security tools like Nmap, Metasploit and Wireshark
- **Linux vs Windows** — Linux is free, more secure, highly customisable and has a powerful terminal
- **Linux Distributions** — different versions of Linux built for different purposes (Kali for hacking, Ubuntu for desktop)
- **Why Ethical Hackers prefer Linux** — complete system control, pre-installed security tools and powerful terminal scripting
