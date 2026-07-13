
# Phase D – Independent Extension

## Objective

The objective of this phase was to extend Linux command-line knowledge by developing a reusable Bash-based enumeration toolkit. The script automates the collection of important system information that is commonly gathered during the initial stages of a penetration test or post-exploitation assessment.

Automation reduces repetitive manual work, improves consistency, and enables Red Team operators to quickly understand the target environment before conducting further security testing.

---

# Introduction

Enumeration is one of the first activities performed after gaining access to a Linux system. Rather than executing numerous commands individually, Bash scripting allows multiple tasks to be combined into a single tool.

The custom toolkit developed during this phase gathers operating system information, user details, network configuration, and file permission summaries in one execution.

This approach reflects real-world Red Team methodology, where automation improves efficiency and reduces the likelihood of overlooking important information.

---

# Enumeration Toolkit Overview

The toolkit was developed as a Bash script named:

```text
enum_toolkit.sh
```

The script performs the following tasks:

- Collects operating system information.
- Displays kernel details.
- Enumerates network interfaces.
- Lists logged-in users.
- Displays home directory permissions.
- Uses color-coded output for improved readability.

---

# Enumeration Toolkit Script

```bash
#!/bin/bash

# ==========================
# Linux Enumeration Toolkit
# ==========================

RED='\033[1;31m'
GREEN='\033[1;32m'
YELLOW='\033[1;33m'
BLUE='\033[1;34m'
NC='\033[0m'

echo -e "${BLUE}========== Linux Enumeration Toolkit ==========${NC}"

echo -e "\n${GREEN}[+] System Information${NC}"
uname -a

echo -e "\n${GREEN}[+] Hostname${NC}"
hostname

echo -e "\n${GREEN}[+] Current User${NC}"
whoami

echo -e "\n${GREEN}[+] Logged-in Users${NC}"
who

echo -e "\n${GREEN}[+] Network Interfaces${NC}"
ip a

echo -e "\n${GREEN}[+] Home Directory Permissions${NC}"
ls -l /home

echo -e "\n${GREEN}[+] Mounted File Systems${NC}"
df -h

echo -e "\n${GREEN}[+] Running Processes${NC}"
ps aux | head

echo -e "\n${GREEN}[+] Enumeration Complete${NC}"
```

---

# Script Execution

The toolkit was made executable using:

```bash
chmod +x enum_toolkit.sh
```

Execution:

```bash
./enum_toolkit.sh
```

The script successfully displayed system information in a structured and color-coded format.

---

# Modules Included

| Module | Purpose |
|----------|---------|
| `uname -a` | Display kernel and operating system information |
| `hostname` | Identify the system hostname |
| `whoami` | Display the current user |
| `who` | List logged-in users |
| `ip a` | Display network interfaces |
| `ls -l /home` | Review file and directory permissions |
| `df -h` | Display mounted file systems |
| `ps aux` | Show running processes |

---

# Practical Applications

The enumeration toolkit supports several common Red Team activities, including:

- Initial system reconnaissance
- Post-exploitation information gathering
- Privilege escalation preparation
- Network assessment
- Security auditing
- Incident response support

The script reduces manual effort while ensuring important information is collected consistently.

---

# Observations

Developing the enumeration toolkit demonstrated how Bash scripting can automate repetitive administrative and security tasks.

Rather than executing commands individually, the toolkit produces a consolidated overview of the target system, allowing analysts to identify potential attack vectors more efficiently.

The addition of ANSI color formatting improves readability and makes it easier to distinguish different sections of the output.

---

# Evidence

### Screenshot 1 – Enumeration Toolkit Source Code

> ![[q27.png]]

---

### Screenshot 2 – Toolkit Execution

![[q28.png]]

---

### Screenshot 3 – Color-Coded Output

![[q29.png]]

---

# Key Takeaways

- Bash scripting enables efficient automation of repetitive tasks.
- Enumeration is a critical phase of every penetration test.
- Automating reconnaissance improves consistency and reduces human error.
- Color-coded output enhances readability during assessments.
- Reusable scripts become valuable additions to a Red Team toolkit.

---

# Phase Summary

This phase successfully extended Linux command-line skills by developing a custom Bash-based enumeration toolkit. The script automated the collection of system information, network details, user information, and file permissions, providing a reusable utility for future penetration testing and Red Team engagements.

The practical experience gained through scripting reinforces the importance of automation in offensive security and demonstrates how simple Bash scripts can significantly improve operational efficiency.