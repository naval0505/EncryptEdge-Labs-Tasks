
# Phase E – Hosted Labs

## Objective

The objective of this phase was to reinforce Linux command-line skills through guided hands-on laboratories. These exercises focused on Linux navigation, file permissions, system enumeration, SSH usage, and Bash scripting within realistic environments used by Red Team operators.

The hosted labs provided practical experience that complemented the concepts learned throughout previous phases and demonstrated how Linux knowledge is applied during penetration testing engagements.

---

# Hosted Lab Environment

| Platform | Details |
|----------|---------|
| Primary Platform | TryHackMe |
| Operating System | Kali Linux |
| Terminal | Bash |
| Additional Practice | HackMyVM Linux Machines |
| Skill Focus | Linux Fundamentals & Enumeration |

---

# Lab 1 – TryHackMe Linux Fundamentals Part 1

## Objective

The Linux Fundamentals Part 1 room introduced the Linux operating system, terminal navigation, and essential file management commands.

### Topics Covered

- Linux filesystem hierarchy
- File and directory navigation
- Hidden files
- Creating and deleting files
- Reading file contents
- Command-line navigation

### Commands Practiced

```bash
pwd
ls
ls -la
cd
touch
mkdir
rm
cat
less
```

### Skills Developed

- Efficient terminal navigation
- Understanding Linux directory structure
- Managing files and folders
- Reading system documentation
- Working entirely from the command line

---

# Lab 2 – Linux Enumeration Practice

Additional Linux practice was completed while solving vulnerable Linux machines.

Activities included:

- Directory enumeration
- File permission analysis
- Searching for configuration files
- Identifying SUID binaries
- Reviewing user accounts
- Reading sensitive files
- System information gathering

Frequently used commands included:

```bash
find
grep
strings
file
chmod
whoami
hostname
uname -a
```

---

# Practical Applications

The knowledge gained during the hosted labs was directly applied throughout previous penetration testing exercises.

Examples included:

- Enumerating Linux targets
- Reading configuration files
- Identifying privilege escalation opportunities
- Navigating unfamiliar file systems
- Executing Bash commands efficiently
- Automating repetitive enumeration tasks

These skills proved valuable during HackMyVM and other Linux-based security challenges.

---

# New Commands Learned

Several commands became part of the regular penetration testing workflow.

| Command | Purpose |
|----------|---------|
| `find` | Locate files and directories |
| `grep` | Search text within files |
| `strings` | Extract readable text from binaries |
| `chmod` | Modify file permissions |
| `ip a` | Display network interfaces |
| `ss -tulpn` | Display listening ports |
| `ps aux` | View running processes |
| `df -h` | Display disk usage |

---

# Key Learning Outcomes

The hosted laboratories reinforced several important concepts:

- Linux command-line proficiency improves efficiency during engagements.
- Understanding permissions is essential for privilege escalation analysis.
- Enumeration should be systematic and repeatable.
- Bash scripting can automate repetitive tasks.
- Documentation is an important part of every penetration test.

---

# Evidence

### Screenshot 1 – TryHackMe Linux Fundamentals Completion

![[q30.png]]

---

### Screenshot 2 – Linux Enumeration Terminal

![[q32.png]]

---

### Screenshot 3 – Bash Script Execution

![[q29.png]]

---

# Practical Observations

The hosted laboratories demonstrated that strong Linux fundamentals are essential for every stage of a penetration test. Nearly every offensive security activity—from reconnaissance to privilege escalation—relies on efficient command-line usage and a solid understanding of the Linux operating system.

Repeated exposure to Linux environments through TryHackMe and vulnerable virtual machines significantly improved speed, confidence, and familiarity with common administrative and security-related commands.

---

# Phase Summary

This phase reinforced Linux command-line knowledge through practical exercises performed in guided laboratory environments. The combination of TryHackMe training, Kali Linux usage, and Linux-based penetration testing practice strengthened core skills in navigation, file management, enumeration, permissions, and automation.

The experience gained during these labs provides a solid operational foundation for future Red Team engagements, privilege escalation assessments, and advanced Linux security testing.