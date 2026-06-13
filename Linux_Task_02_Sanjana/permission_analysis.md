# Part E — Permission Analysis

**Submitted by:** Sanjana
**Date:** 12 June 2026

---

## How to Read Linux Permissions

Linux permissions are shown as 3 sets of 3 characters: `rwxrwxrwx`
- First set → **Owner** rights
- Second set → **Group** rights
- Third set → **Others** rights

`r` = read, `w` = write, `x` = execute, `-` = no permission

In numeric form: `r=4`, `w=2`, `x=1`

---

## 755
**Symbolic:** `rwxr-xr-x`

| Who | Rights |
|-----|--------|
| Owner | Read, Write, Execute (7 = 4+2+1) |
| Group | Read, Execute (5 = 4+1) |
| Others | Read, Execute (5 = 4+1) |

**Real-world use case:** Used for executable scripts and program files. The owner can modify the file, but everyone else can only run and read it. Commonly used for web server directories and system scripts.

---

## 644
**Symbolic:** `rw-r--r--`

| Who | Rights |
|-----|--------|
| Owner | Read, Write (6 = 4+2) |
| Group | Read only (4) |
| Others | Read only (4) |

**Real-world use case:** Used for regular files like configuration files, HTML files and documents. The owner can edit them but others can only read them. This is the default permission for most files.

---

## 777
**Symbolic:** `rwxrwxrwx`

| Who | Rights |
|-----|--------|
| Owner | Read, Write, Execute (7) |
| Group | Read, Write, Execute (7) |
| Others | Read, Write, Execute (7) |

**Real-world use case:** Gives everyone full access. This is considered very dangerous and should almost never be used on sensitive files. Sometimes used temporarily during development but must be changed before going to production.

---

## 600
**Symbolic:** `rw-------`

| Who | Rights |
|-----|--------|
| Owner | Read, Write (6 = 4+2) |
| Group | No access (0) |
| Others | No access (0) |

**Real-world use case:** Used for highly sensitive files like SSH private keys, password files and personal configuration files. Only the owner can read or modify the file — no one else has any access at all.

---

## 700
**Symbolic:** `rwx------`

| Who | Rights |
|-----|--------|
| Owner | Read, Write, Execute (7) |
| Group | No access (0) |
| Others | No access (0) |

**Real-world use case:** Used for private scripts and executable files that only the owner should run. Common for personal home directories and private automation scripts. No other user can even see the contents.
