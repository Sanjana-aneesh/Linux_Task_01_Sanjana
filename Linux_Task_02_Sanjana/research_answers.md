# Part G — Linux Security Research

**Submitted by:** Sanjana
**Date:** 12 June 2026

---

### 1. Why are file permissions important?
File permissions control who can read, write or execute a file on a Linux system. Without proper permissions, any user on the system could read, modify or delete files they shouldn't have access to. Permissions are the first line of defence in Linux security — they prevent unauthorised users from accessing sensitive data, stop malicious programs from modifying system files, and ensure that only trusted users can run certain scripts or commands. In a multi-user environment like a server, permissions are what keep one user's data safe from another.

### 2. What happens if sensitive files are given 777 permissions?
Giving a sensitive file `777` permissions means every single user on the system — including attackers or malicious programs — can read, modify and execute it. This is extremely dangerous. For example if a password file is given `777`, any user logged into the system can open it and steal the passwords. If a script is given `777`, anyone can modify it to add malicious code and then run it. Real-world attacks have exploited `777` permissions to escalate privileges, steal data and take over systems. It should almost never be used on sensitive files.

### 3. What is the principle of Least Privilege?
The principle of Least Privilege means giving a user, program or process only the minimum level of access they need to do their job — nothing more. For example, a web server only needs to read website files, so it should have read-only access — not write or execute permissions on the whole system. This principle limits the damage that can happen if an account is compromised. If an attacker gains access to an account with minimal privileges, they can't do much. But if they gain access to an account with full access, they can cause serious damage. Least Privilege is one of the most important concepts in cybersecurity.

### 4. Why do organisations restrict user access?
Organisations restrict user access for several important reasons. First, it protects sensitive data — employees should only see information relevant to their role. A marketing employee doesn't need access to financial records or server configurations. Second, it reduces the risk of insider threats — limiting access means even a malicious insider can only damage what they have access to. Third, it contains the damage from external attacks — if a hacker compromises one account, restricted permissions stop them from moving freely through the entire system. Finally, many industries have legal requirements like GDPR and HIPAA that require organisations to control who can access sensitive data. Restricting access is not just good practice — it is often a legal requirement.
