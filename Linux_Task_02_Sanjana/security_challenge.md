# Part F — Security Challenge

**Submitted by:** Sanjana
**Date:** 12 June 2026

---

## Scenario
I am a Linux Administrator responsible for securing files on a system.

---

## Recommended Permissions Table

| File | Recommended Permission | Reason |
|------|----------------------|--------|
| `password_backup.txt` | `600` (`rw-------`) | This file contains sensitive passwords. Only the owner should be able to read or edit it. No other user — not even group members — should have any access at all. |
| `public_notice.txt` | `644` (`rw-r--r--`) | This is a public document meant for everyone to read. The owner can edit it but all other users can only read it. No one needs execute permission on a text file. |
| `system_log.txt` | `640` (`rw-r-----`) | System logs should be readable by the admin and group members for monitoring, but completely hidden from other users to prevent attackers from reading system activity. |
| `personal_notes.txt` | `600` (`rw-------`) | Personal notes are private to the owner only. No other user should be able to read, write or execute this file. |

---

## Reasoning

- **password_backup.txt** gets `600` because passwords are the most sensitive information on a system. If anyone else could read this file, they could compromise the entire system. The principle of least privilege means giving only the minimum access needed.

- **public_notice.txt** gets `644` because it is meant to be shared and read by everyone. The owner needs write access to update the notice, but no one else needs to modify it.

- **system_log.txt** gets `640` because administrators and their team need to monitor logs, but regular users and outsiders should not be able to see what the system is doing. This also prevents attackers from covering their tracks by reading logs.

- **personal_notes.txt** gets `600` because personal files are private. Only the owner should ever access their own personal notes.
