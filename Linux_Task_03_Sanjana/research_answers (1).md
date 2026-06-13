# Research Answers — Linux Task 03

**Submitted by:** Sanjana
**Date:** 13 June 2026

---

## Part F — Security Monitoring Commands

### 1. netstat
**Purpose:** Displays active network connections, listening ports and network statistics.
**Example Output:**
```
Proto  Local Address    Foreign Address   State
tcp    0.0.0.0:22       0.0.0.0:*         LISTEN
tcp    192.168.1.1:80   10.0.0.5:54321    ESTABLISHED
```
**Security Use Case:** Used to detect suspicious open ports or unexpected outbound connections. If a port is open that shouldn't be, it could indicate malware or an unauthorised service.

---

### 2. ss
**Purpose:** A faster modern replacement for netstat. Shows socket statistics and active network connections.
**Example Output:**
```
Netid  State   Local Address:Port   Peer Address:Port
tcp    LISTEN  0.0.0.0:22           0.0.0.0:*
tcp    ESTAB   192.168.1.2:43210    142.250.1.1:443
```
**Security Use Case:** Used to quickly check all open ports and active connections on a system. Security analysts use it to identify unusual connections that could indicate a breach or data exfiltration.

---

### 3. who
**Purpose:** Shows which users are currently logged into the system.
**Example Output:**
```
kali     pts/0    2026-06-13 05:00 (:0)
root     pts/1    2026-06-13 05:45 (192.168.1.5)
```
**Security Use Case:** Used to detect unauthorised logins. If an unknown user or an unexpected remote login appears, it could indicate a security breach.

---

### 4. w
**Purpose:** Shows who is logged in and what they are currently doing, including CPU usage and idle time.
**Example Output:**
```
USER   TTY   FROM         LOGIN@   IDLE   WHAT
kali   pts/0  :0          05:00    0.00s  w
root   pts/1  192.168.1.5  05:45   2:00   bash
```
**Security Use Case:** More detailed than `who` — shows exactly what each logged in user is doing. Useful for detecting suspicious activity like a user running unexpected commands.

---

### 5. last
**Purpose:** Shows a history of all previous logins and logouts on the system.
**Example Output:**
```
kali   pts/0   :0          Fri Jun 13 05:00  still logged in
root   pts/1   192.168.1.5 Thu Jun 12 22:00 - 23:00 (01:00)
```
**Security Use Case:** Used to audit login history and detect unusual login patterns like logins at odd hours, from unknown IP addresses or multiple failed attempts. Essential for incident response.

---

## Part G — Mini SOC Activity

### Scenario: System is running slowly

**1. How would you identify resource-heavy processes?**
I would start by running `top` or `htop` to get a real-time view of all running processes sorted by CPU and memory usage. The process at the top of the list is consuming the most resources. I would also run `free -h` to check if the system is running low on memory and `df -h` to check if disk space is full — both can cause slowdowns. `ps aux --sort=-%cpu` would also help sort all processes by CPU usage to find the heaviest ones.

**2. How would you determine whether a process is suspicious?**
I would look at several things. First, check if the process name is recognisable — unknown or randomly named processes are suspicious. Second, check which user is running it — a system process running under a regular user account is a red flag. Third, check the CPU and memory usage — a process using unusually high resources for no clear reason could be malware like a cryptominer. I would also use `ls -l /proc/PID` to find the actual file the process is running from and check if it's in an unusual location like `/tmp`.

**3. What information would you collect before terminating a process?**
Before terminating any process I would collect: the PID, the process name and command, the user running it, the CPU and memory usage, how long it has been running, any open network connections using `ss` or `netstat`, and the parent process ID (PPID). I would also take a screenshot or log all of this information for documentation. This is important because terminating a legitimate system process could crash the system, and the collected information helps determine whether the process is genuinely suspicious or just resource-heavy for a valid reason.
