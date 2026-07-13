
# Phase B – Setup Homelab / Target

## Objective

The objective of this phase was to prepare the Linux environment for remote system interaction by configuring an SSH client, establishing a secure remote connection, and documenting the workflow used to access Linux systems during Red Team operations.

Secure Shell (SSH) is one of the most important protocols used by penetration testers, system administrators, and Red Team operators for secure remote administration and post-exploitation activities.

---

# Introduction

SSH (Secure Shell) is a cryptographic network protocol that enables secure communication between systems over an encrypted channel. It provides confidentiality, integrity, and authentication while allowing administrators and security professionals to remotely manage Linux systems.

Throughout penetration testing engagements, SSH is frequently used for:

- Remote administration
- Accessing compromised Linux hosts
- Secure file transfers
- Privilege escalation activities
- Tunnel creation and port forwarding

Mastering SSH is an essential skill for every Red Team operator.

---

# Laboratory Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Shell | Bash |
| Remote Protocol | SSH |
| Target | Linux Lab Machine (OverTheWire Bandit / HackMyVM) |
| Terminal | Kali Linux Terminal |

---

# SSH Connection

The remote system was accessed using the standard SSH client available in Linux.

Example syntax:

```bash
ssh username@target_ip
```

For OverTheWire Bandit:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

For a local laboratory or HackMyVM target:

```bash
ssh user@192.168.x.x
```

Once authenticated, the remote Linux shell became available for enumeration and command execution.

---

# Initial Enumeration

After establishing the SSH session, several basic commands were used to identify the environment.

Examples included:

```bash
pwd
```

```bash
whoami
```

```bash
hostname
```

```bash
uname -a
```

```bash
ls -la
```

These commands provide valuable information regarding the current user, system configuration, kernel version, and available files.

---

# Secure Progress Tracking

Throughout the exercise, important findings and passwords were documented in a local progress file for future reference.

Example:

```text
bandit_progress.txt
```

Maintaining organized notes improves workflow efficiency and supports professional documentation during penetration testing engagements.

---

# Importance of SSH in Red Team Operations

SSH is used extensively during offensive security assessments because it enables secure interaction with remote Linux systems.

Common Red Team use cases include:

- Remote system administration
- Privilege escalation
- File transfers using SCP/SFTP
- Reverse SSH tunneling
- Remote command execution
- Internal network pivoting

Understanding SSH authentication and secure session management is essential for both offensive and defensive security professionals.

---

# Practical Observations

Establishing a secure remote connection demonstrated how Linux systems are commonly administered within enterprise environments.

Using SSH instead of physical access allows Red Team operators to safely perform reconnaissance, execute commands, collect evidence, and automate administrative tasks while maintaining encrypted communications.

The exercise also reinforced the importance of securely storing credentials and maintaining detailed progress notes during long-term engagements.

---

# Evidence

### Screenshot 1 – Successful SSH Login

> ![[q19.png]]
---

### Screenshot 2 – Initial Enumeration

>![[q20.png]]

---

### Screenshot 3 – Progress Notes

![[q21.png]]
---

# Key Takeaways

- SSH provides secure remote access to Linux systems.
- Proper authentication protects administrative sessions.
- Initial system enumeration is an essential first step after gaining access.
- Organized documentation improves repeatability and reporting quality.
- SSH is one of the most frequently used protocols in professional Red Team operations.

---

# Phase Summary

This phase focused on establishing secure remote connectivity using SSH and preparing the Linux environment for further enumeration and operational activities. By successfully connecting to a remote Linux system, performing basic reconnaissance, and documenting observations, the foundational skills required for remote system administration and penetration testing were reinforced.

These skills form the basis for more advanced activities such as privilege escalation, Bash scripting, automation, and post-exploitation in subsequent phases.