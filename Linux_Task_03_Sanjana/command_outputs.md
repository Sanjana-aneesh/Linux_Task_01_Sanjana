# Command Outputs — Linux Task 03

**Submitted by:** Sanjana
**Date:** 13 June 2026

---

## Part A — Process Monitoring

### ps
**Purpose:** Shows processes running in the current terminal session.
**Output:**
```
  PID TTY          TIME CMD
 7321 pts/0    00:00:14 zsh
236185 pts/0   00:00:00 ps
```

### ps aux
**Purpose:** Shows all running processes on the system with detailed info including CPU and memory usage.
**Output:** Shows all processes for all users with PID, CPU%, MEM%, and command.

### top
**Purpose:** Real-time interactive process viewer showing CPU, memory usage and all running processes.
**Output:**
```
top - 04:10:26 up 8:23, 1 user, load average: 0.25, 0.30, 0.28
Tasks: 216 total, 1 running, 215 sleeping, 0 stopped, 0 zombie
%Cpu(s): 5.0 us, 10.1 sy, 84.5 id
MiB Mem: 1971.7 total, 175.6 free, 1054.8 used
```

### htop
**Purpose:** An enhanced interactive process viewer with colour coding and easier navigation than top.
**Output:** Shows processes with CPU bars, memory bars and colour coded process list.

### Answers

**1. What is a Process?**
A process is a running instance of a program. Every time you open an application or run a command, the operating system creates a process for it. Each process has its own memory space and gets assigned a unique PID.

**2. What is a PID?**
PID stands for Process ID. It is a unique number assigned by the operating system to every running process. It is used to identify and manage processes — for example when you want to terminate a specific process you use its PID.

**3. Which process is consuming the most CPU?**
`Xorg` (PID 851) was consuming the most CPU at **13.9%** as shown in the top output.

**4. Which process is consuming the most Memory?**
`Xorg` (PID 851) was also consuming the most memory at **10.8%** as shown in the top output.

---

## Part B — Process Management

### Commands Used
```
sleep 300 &          # Start sleep in background
ps aux | grep sleep  # Find the process
kill 255573          # Terminate gracefully
sleep 300 &          # Start new sleep
kill -9 259045       # Force terminate
```

### Documentation

| Field | Value |
|-------|-------|
| PID Found | `259045` |
| Command Used | `kill -9 259045` |
| Result | `[1] + killed sleep 300` — process forcefully terminated |

**Difference between kill and kill -9:**
- `kill PID` sends a SIGTERM signal — asks the process to terminate gracefully
- `kill -9 PID` sends SIGKILL — forcefully terminates the process immediately with no cleanup

---

## Part C — System Monitoring

### free -h
**Purpose:** Shows RAM and swap memory usage in human readable format.
**Output:**
```
       total   used   free  shared  buff/cache  available
Mem:   1.9Gi  1.3Gi  127Mi   46Mi       764Mi      664Mi
Swap:  953Mi   19Mi  933Mi
```

### df -h
**Purpose:** Shows disk space usage of all mounted filesystems.
**Output:**
```
Filesystem  Size  Used  Avail  Use%  Mounted on
/dev/sda1    79G   16G    59G   22%  /
```

### uptime
**Purpose:** Shows how long the system has been running, number of users and load average.
**Output:**
```
04:54:25 up 9:07, 1 user, load average: 0.07, 0.21, 0.24
```

### uname -a
**Purpose:** Shows complete system and kernel information.
**Output:**
```
Linux kali 6.18.12+kali-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.18.12-1kali1 (2026-02-25) x86_64 GNU/Linux
```

### System Summary

| Field | Value |
|-------|-------|
| Total RAM | 1.9GiB |
| Available RAM | 664MiB |
| Disk Size | 79G |
| Disk Used | 16G (22%) |
| System Uptime | 9 hours 7 minutes |
| Kernel Version | Linux kali 6.18.12+kali-amd64 |

---

## Part D — Service Monitoring

### systemctl status ssh
**Purpose:** Checks the status of the SSH service.
**Output:**
```
ssh.service - OpenBSD Secure Shell server
Loaded: loaded; disabled; preset: disabled
Active: inactive (dead)
```

### systemctl status NetworkManager
**Purpose:** Checks the status of the NetworkManager service.
**Output:**
```
NetworkManager.service - Network Manager
Loaded: loaded; enabled; preset: enabled
Active: active (running) since Fri 2026-06-12 00:35:21 EDT
Main PID: 754 (NetworkManager)
```

### Answers

**1. What is a Service?**
A service is a background program that runs continuously to perform a specific function — like providing network connectivity, handling SSH connections or managing system logs. Services start automatically when the system boots and run without user interaction.

**2. Why are services important?**
Services handle critical system functions that need to run all the time. Without the NetworkManager service for example, your device would lose internet connectivity. Without SSH service, remote access to the server would be impossible. Services keep the system functional and accessible.

**3. How can a stopped service affect a system?**
If a critical service stops, the functionality it provides becomes unavailable. For example if NetworkManager stops, the system loses network connectivity. If SSH stops, remote administrators cannot connect to manage the server. In a production environment, a stopped service can cause downtime, data loss or security vulnerabilities.

---

## Part E — Shell Script

### Script: system_report.sh
```bash
#!/bin/bash
echo "================================"
echo "     System Information Report  "
echo "================================"
echo "User: $(whoami)"
echo "Hostname: $(hostname)"
echo "Date: $(date)"
echo "Current Directory: $(pwd)"
echo ""
echo "Memory Usage:"
free -h
echo ""
echo "Disk Usage:"
df -h
echo "================================"
```

### Execution
```
chmod +x system_report.sh
./system_report.sh
```

### Output
```
================================
     System Information Report  
================================
User: kali
Hostname: kali
Date: Sat Jun 13 05:13:15 AM EDT 2026
Current Directory: /home/kali

Memory Usage:
       total    used    free  available
Mem:   1.9Gi   1.3Gi   124Mi     605Mi

Disk Usage:
/dev/sda1   79G   16G   59G   22%   /
================================
```
