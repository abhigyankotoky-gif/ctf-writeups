# [Challenge Name] — [Platform] [Level/Category]
 
> **Platform:** OverTheWire Bandit / PicoCTF / BreachLab Ghost  
> **Level/Challenge:** e.g., Bandit Level 5 → 6  
> **Category:** e.g., Linux Basics / Web / Cryptography / Forensics / Reverse Engineering  
> **Difficulty:** Easy / Medium / Hard  
> **Date Completed:** YYYY-MM-DD  
 
---
 
## Challenge Description
 
> Paste the original challenge prompt here, verbatim.
 
---
 
## Initial Observations
 
What did you notice first? What stood out when you read the challenge?
 
- Observation 1
- Observation 2
- Any hints baked into the challenge text?
---
 
## Approach
 
How did you decide what to try? What was your mental model going in?
 
---
 
## Solution Walkthrough
 
Step-by-step. Write as if explaining to yourself six months from now.
 
### Step 1 — [Short label]
 
```bash
# command you ran
$ ssh bandit5@bandit.labs.overthewire.org -p 2220
```
 
What this does and why you ran it.
 
### Step 2 — [Short label]
 
```bash
$ find . -type f -size 1033c ! -executable
```
 
Explain the flags/options you used. Don't just dump the command.
 
### Step 3 — [Short label]
 
```bash
$ cat ./inhere/.file07
```
 
---
 
## Dead Ends & Wrong Turns
 
What did you try that *didn't* work? This is the most useful part.
 
- Tried `ls -la` first, found too many files → needed `find` with filters
- Assumed the file was in the home directory → it was in a subdirectory
---
 
## Flag / Answer
 
```
password: [REDACT if publishing publicly, store locally]
```
 
---
 
## Concepts Used
 
| Concept | What It Is | Why It Mattered Here |
|---------|-----------|----------------------|
| `find` with filters | Linux file search utility | Narrowed 1000 files to 1 |
| File permissions | Unix r/w/x bits | Challenge required non-executable |
 
---
 
## What I Learned
 
One paragraph. Not a list. Force yourself to synthesize.
 
What clicked that you didn't understand before? What would you do differently? What does this connect to?
 
---
 
## Resources That Helped
 
- [Link or book/man page name]
- `man find` — the `-size` flag explanation
 