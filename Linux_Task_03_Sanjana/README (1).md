# Linux Task 03 — Process Management, System Monitoring & Basic Shell Scripting

**Intern:** Sanjana
**Date:** 13 June 2026
**Organization:** White Band Associates
**OS:** Kali Linux 2026.1 on Oracle VirtualBox

---

## 📁 Repository Structure

| File/Folder | Description |
|-------------|-------------|
| `Screenshots/` | All screenshots for Part A, B, C, D & E |
| `Shell_Script/system_report.sh` | Part E — Shell script file |
| `System_Report/system_report.md` | Part C — System summary report |
| `Command_Outputs/command_outputs.md` | Part A, B, C, D & E — All command outputs and answers |
| `Research_Answers/research_answers.md` | Part F & G — Security monitoring research and SOC activity |

---

## 📋 Summary of Findings

### 🔍 Part A — Process Monitoring
Ran four process monitoring commands. `ps` showed only the processes in the current terminal session. `ps aux` listed all running processes across all users with their CPU and memory usage. `top` showed a real-time view of 216 running tasks with load average of 0.25. `htop` provided a colour-coded interactive view of all processes. The process consuming the most CPU and Memory was `Xorg` (PID 851) at **13.9% CPU** and **10.8% Memory**. A process is a running instance of a program and each one is identified by a unique PID (Process ID).

### ⚙️ Part B — Process Management
Started `sleep 300` as a background process using `&`. Used `ps aux | grep sleep` to find it with PID **259045**. Terminated it gracefully using `kill 255573` first, then started a new sleep and force killed it using `kill -9 259045`. The terminal confirmed `[1] + killed sleep 300`. The difference is that `kill` sends SIGTERM (graceful shutdown) while `kill -9` sends SIGKILL (immediate forced termination).

### 💻 Part C — System Monitoring
Collected complete system information using 4 commands:
- **Total RAM:** `1.9GiB` | **Available:** `664MiB`
- **Disk:** `79G` total, `16G` used, `59G` free (22% used)
- **Uptime:** `9 hours 7 minutes, 1 user`
- **Kernel:** `Linux kali 6.18.12+kali-amd64 x86_64 GNU/Linux`

### 🔧 Part D — Service Monitoring
Checked two services using `systemctl`. SSH service was `inactive (dead)` and disabled — meaning remote SSH access is not available. NetworkManager was `active (running)` since Jun 12 with PID 754 — handling all network connectivity. A stopped service can cause loss of functionality — if NetworkManager stopped, the system would lose internet access.

### 📝 Part E — Shell Scripting
Created and executed `system_report.sh` — a bash script that automatically collects and displays system information including current user, hostname, date and time, current directory, memory usage and disk usage. The script was made executable using `chmod +x` and executed with `./system_report.sh`.

### 🔒 Part F — Security Monitoring Research
Researched 5 security monitoring commands:
- `netstat` — shows active network connections and open ports
- `ss` — faster modern replacement for netstat
- `who` — shows currently logged in users
- `w` — shows logged in users and what they are doing
- `last` — shows login history for all users
All are essential tools for detecting suspicious network activity and unauthorised access.

### 🛡️ Part G — Mini SOC Activity
As a Security Analyst investigating a slow system, I would use `top`/`htop` to identify resource-heavy processes, check for unknown process names and unusual user ownership to spot suspicious activity, and collect the PID, process name, user, CPU/memory usage, network connections and parent process details before terminating anything. Collecting this information first is critical for proper incident documentation and to avoid accidentally stopping a legitimate system process.
