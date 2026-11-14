
# First Contact — BreachLab Ghost Level 0 → 1
 
> **Platform:** BreachLab  
> **Track:** Ghost  
> **Level:** 0 → 1  
> **Challenge Name:** First Contact  
> **Category:** Linux Basics / Reconnaissance  
> **Points:** 100 pts + 25 First Blood Bonus  
> **Date Completed:** 2026-11-14  
 
---
 
## Challenge Description
 
> The previous analyst left in a hurry.  
> His terminal is still open. His files — still here.  
> Find what he left behind.
 
**Goal:** Retrieve the password for ghost1  
**Connect:** `ssh ghost1@204.168.229.209 -p 2222`
 
**Topics to read before:** `ls`, `cat`, `cd`
 
---
 
## Walkthrough
 
We have a blank screen in front of us, to first check which directory we are in , we run the `pwd` command.
 
```bash
pwd
```
 
```
/home/ghost0
```
 
Now, we try to find some files that may have been left in the open ( as the instructions said ).
We run the command `ls` to list all files and directories. We get a file and a directory.
 
```bash
ls
```
 
```
README  workspace
```
 
The README file is just shouting at me to open it , so i do just that using the `cat` command.
 
```bash
cat README
```
 
```
ANALYST WORKSTATION - KAEL
Last active: 2026-03-28 02:47 UTC
Status : Abandoned
 
If you're reading this, you found my terminal.
I left in a hurry. Didn't have time to clean up.
Nothing in this shell is hidden. It's just here.
If you can't see it, you're not looking hard enough.
Don't leave traces.
-KAEL.
```
 
Well , finally that was something.
So , now we know that everything in this shell is exposed and what we are finding is out in the open and we just have to look properly.
Now , we open up the workspace directory using —
 
```bash
cd workspace
```
 
We list everything with `ls`, which gives us —
 
```bash
ls
```
 
```
archive  notes.txt
```
 
Let's first open `notes.txt`.
 
```bash
cat notes.txt
```
 
```
OPERATIONAL NOTES — KAEL
========================
Target: internal network segment 10.4.x.x
Method: passive recon, no active scanning
Status: ongoing
 
Credentials filed separately in archive/.
Do not store passwords in plaintext notes.
```
 
Since it tells us credentials are filed separately in `archive/`, we open archive using —
 
```bash
cd archive
ls
```
 
```
credentials
```
 
We open it using —
 
```bash
cat credentials
```
 
We found the password for Ghost1.
 
The password was sitting right in the open — no encryption, no obfuscation, just an abandoned workstation with its files left open. KAEL didn't hide anything. He just left.
 
The challenge was actually about what you should do whenever faced with any unfamiliar box , your first move shouldn't be running some fancy tools. It's to look at what's already there. `ls`, `cat`, `cd` — three commands, and the whole picture unfolds. Every real engagement starts exactly this way.
 
---
 
## Flag / Answer
 
```
ghost1 password: [stored locally]
```
 
---
 
## Concepts Used
 
| Concept | What It Is | Why It Mattered Here |
|---------|-----------|----------------------|
| `pwd` | Prints your current working directory path | First move on an unfamiliar box — know where you are before you move |
| `ls` | Lists files and directories at the current location | Revealed `README` and `workspace` at each level of the directory tree |
| `cat` | Displays file contents in the terminal | Used to read `README`, `notes.txt`, and `credentials` — the core action of this challenge |
| `cd` | Changes your current directory | Allowed navigation from home → workspace → archive |
| Filesystem hierarchy | Unix organises files in a nested tree of directories | The credentials were three levels deep — understanding the tree is what made them findable |
| Passive reconnaissance | Gathering information by reading what's already present, without active probing | KAEL left everything in the open — reading existing files is the most basic form of passive recon |
 
---
 
## What I Learned
 
This level helped me get familiar with basic Linux terminal commands such as "ls", "cd", and "cat" to navigate directories and inspect files. I learned how to explore an unfamiliar machine, identify relevant files, and retrieve information from them rather than randomly guessing where the flag might be.

I also understood how SSH is used to access a remote machine and how the credentials obtained at one level can be used to progress to the next. More importantly, it reinforced the habit of carefully reading the environment — treating every file, directory name, and piece of leftover context as a potential clue rather than noise.
 
---
 
## Resources That Helped
 
- [`man ls`](https://man7.org/linux/man-pages/man1/ls.1.html)
- [`man cat`](https://man7.org/linux/man-pages/man1/cat.1.html)
- [`man cd`](https://ss64.com/bash/cd.html)
 