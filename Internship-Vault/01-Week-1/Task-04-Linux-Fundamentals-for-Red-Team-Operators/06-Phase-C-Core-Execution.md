
# Phase C – Core Execution

## Objective

The objective of this phase was to apply Linux enumeration techniques, understand file permissions, and automate reconnaissance tasks using Bash scripting. This phase focused on identifying files, analyzing permissions, extracting information, and creating reusable scripts commonly used during penetration testing engagements.

---

# Introduction

Enumeration is one of the most critical stages of a penetration test. After obtaining access to a Linux system, attackers and Red Team operators gather information about the operating system, users, services, files, and permissions before attempting privilege escalation or lateral movement.

Linux provides powerful command-line utilities that allow analysts to efficiently search for files, inspect permissions, identify hidden information, and automate repetitive tasks.

---

# Commands Practiced

The following Linux commands were used throughout this phase.

| Command | Purpose |
|----------|---------|
| `find` | Search for files and directories |
| `grep` | Search for patterns within files |
| `file` | Identify file types |
| `strings` | Extract readable strings from binaries |
| `chmod` | Modify file permissions |
| `ls -l` | Display detailed file permissions |
| `cat` | Read file contents |
| `head` | Display the beginning of a file |
| `tail` | Display the end of a file |

These commands are frequently used during Linux enumeration and privilege escalation.

---

# File Permission Analysis

Linux file permissions determine which users can read, write, or execute files.

Example:

```bash
ls -l
```

Sample output:

```text
-rwxr-xr-- 1 kali kali 2456 Jun 12 script.sh
```

Permission breakdown:

- Owner → Read, Write, Execute
- Group → Read, Execute
- Others → Read

Understanding these permissions helps identify misconfigurations that could lead to privilege escalation.

---

# Searching for Files

The `find` command was used to locate files based on permissions and ownership.

Example:

```bash
find /home -type f
```

Search for readable files:

```bash
find / -type f -perm -u=r 2>/dev/null
```

Search for SUID binaries:

```bash
find / -perm -4000 -type f 2>/dev/null
```

These commands are commonly used during Linux privilege escalation assessments.

---

# Bash Automation Script

To automate the discovery of readable files, a Bash script named **find_readables.sh** was created.

```bash
#!/bin/bash

echo "===== Readable Files ====="

find / -type f -perm -u=r -exec ls -l {} \; 2>/dev/null

echo "Enumeration Complete."
```

Execution:

```bash
chmod +x find_readables.sh
```

```bash
./find_readables.sh
```

The script successfully listed readable files while suppressing permission-denied messages.

---

# Practical Applications

The commands practiced during this phase are frequently used in Red Team engagements to:

- Locate configuration files.
- Search for sensitive credentials.
- Identify world-readable files.
- Enumerate SUID binaries.
- Detect privilege escalation opportunities.
- Automate reconnaissance tasks.

These techniques improve efficiency during post-exploitation and system enumeration.

---

# Observations

Automating repetitive Linux commands with Bash scripting significantly reduces manual effort and minimizes human error.

During previous penetration testing exercises on HackMyVM and TryHackMe, these commands proved valuable for quickly locating important files, understanding system permissions, and identifying potential attack paths.

Developing small automation scripts improves consistency and allows Red Team operators to focus on analysis rather than repetitive command execution.

---

# Evidence

### Screenshot 1 – File Enumeration

>![[q22.png]]

---

### Screenshot 2 – Bash Script Execution

> ![[q23.png]]

---

### Screenshot 3 – Permission Analysis

>![[q24.png]]

---

# Key Takeaways

- Linux enumeration is a fundamental stage of every penetration test.
- File permissions play a critical role in system security.
- Bash scripting enables automation of repetitive reconnaissance tasks.
- Commands such as `find`, `grep`, `strings`, and `chmod` are essential tools for Red Team operators.
- Practical experience with Linux command-line utilities improves operational efficiency during security assessments.

---

# Phase Summary

This phase demonstrated the practical application of Linux enumeration techniques and basic Bash scripting within a controlled environment. By combining manual exploration with simple automation, the exercise reinforced core Red Team skills related to reconnaissance, permission analysis, and system enumeration.

These techniques provide a strong foundation for privilege escalation, post-exploitation activities, and advanced automation in future penetration testing engagements.