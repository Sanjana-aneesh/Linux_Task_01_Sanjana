# Notes — Linux Task 01

**Submitted by:** Sanjana
**Date:** 12 June 2026

---

## Things I Learned

- Linux is case sensitive — `cd desktop` and `cd Desktop` are completely different. I made this mistake and learned it the hard way!
- `ls -la` shows hidden files that start with `.` like `.bashrc` and `.profile` — these are important system files that are hidden by default.
- `tree` is a really useful command to visually see the entire folder structure at once.
- `rm` permanently deletes a file — there is no recycle bin in Linux so you have to be careful before deleting anything.
- `mv` can be used for both moving AND renaming a file which is interesting.
- `touch` just creates an empty file without opening it — useful for quickly creating multiple files at once.
- `whoami` and `hostname` both returned `kali` since this is a fresh Kali Linux installation on VirtualBox.
- The terminal prompt `(kali@kali)-[~/Desktop]` shows username, hostname and current directory all at once which is very helpful.
- `history` keeps track of every command you run — useful when you forget what you typed earlier.
- `pwd` is helpful when you get lost in the file system and need to know exactly where you are.

## Observations

- Kali Linux comes with many folders already created like Desktop, Documents, Downloads, Music, Pictures etc — similar to Windows.
- The terminal in Linux is much more powerful than the Command Prompt in Windows.
- Creating multiple folders at once with `mkdir` saves a lot of time.
- Linux file permissions shown in `ls -la` like `drwxr-xr-x` tell you who can read, write or execute a file.
