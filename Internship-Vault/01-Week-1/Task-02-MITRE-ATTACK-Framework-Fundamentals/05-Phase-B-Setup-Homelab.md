
# Phase B – Setup Homelab / Target Environment

## Objective

The objective of this phase was to prepare a secure and isolated laboratory environment for safely executing Atomic Red Team tests. This included configuring the required tools, verifying the execution environment, and performing an initial ATT&CK technique simulation.

---

# Environment Overview

A dedicated lab environment was used to safely emulate attacker techniques without impacting production systems.

| Component | Details |
|-----------|---------|
| Operating System | Windows Virtual Machine |
| Framework | MITRE ATT&CK |
| Tool | Atomic Red Team |
| Shell | PowerShell |
| Repository | Atomic Red Team GitHub |
| Lab Type | Isolated Virtual Machine |
| Purpose | Safe Adversary Emulation |

---

# Lab Preparation

Before executing any Atomic Red Team tests, the laboratory environment was configured with the necessary tools and permissions.

The following preparation steps were completed:

- Created an isolated Windows virtual machine.
- Verified internet connectivity.
- Installed PowerShell.
- Cloned the Atomic Red Team repository.
- Verified execution policy.
- Confirmed administrator privileges.
- Prepared the environment for ATT&CK simulations.

---

# Cloning the Atomic Red Team Repository

The Atomic Red Team repository contains hundreds of small, safe tests that simulate real-world adversary techniques mapped to MITRE ATT&CK.

Repository:

```bash
git clone https://github.com/redcanaryco/atomic-red-team.git
```

Move into the directory:

```bash
cd atomic-red-team
```

---

# PowerShell Execution Policy

To allow execution of Atomic Red Team scripts during the current PowerShell session, the execution policy was temporarily modified.

Command:

```powershell
Set-ExecutionPolicy Bypass -Scope Process
```

This change applies only to the active PowerShell process and does not permanently modify the system configuration.

---

# Initial Atomic Test

The first technique selected for execution was:

| Technique | ATT&CK ID |
|-----------|-----------|
| System Information Discovery | T1082 |

This technique simulates how attackers enumerate system information after gaining access to a machine.

Examples of information gathered include:

- Operating System Version
- Hostname
- CPU Architecture
- System Manufacturer
- Installed Hardware
- BIOS Information

Understanding the target environment helps attackers determine suitable privilege escalation methods, persistence mechanisms, and lateral movement opportunities.

---

# Expected Behavior

Executing the Atomic Red Team simulation should produce output similar to legitimate system discovery commands without causing permanent system changes.

Observable activities include:

- Querying operating system details
- Enumerating hardware information
- Reading system configuration
- Displaying host information

Since these activities resemble legitimate administrative tasks, they are commonly abused by threat actors during post-exploitation.

---

# Security Considerations

To ensure safe testing, the following precautions were followed:

- All tests were executed inside an isolated virtual machine.
- No production infrastructure was involved.
- No malicious payloads were deployed.
- No persistence mechanisms were installed.
- Tests were limited to documented Atomic Red Team procedures.

---

# Evidence

## Screenshot 1 – Atomic Red Team Repository

> *Insert screenshot showing the cloned Atomic Red Team repository.*

---

## Screenshot 2 – PowerShell Execution Policy

> *Insert screenshot showing successful execution of the `Set-ExecutionPolicy` command.*

---

## Screenshot 3 – Atomic Test Execution

> *Insert screenshot showing successful execution of the T1082 atomic test along with the generated output.*

---

# Observations

The Atomic Red Team framework provides a controlled method for reproducing real-world adversary behaviors. During this phase, the execution environment was successfully prepared, and the initial ATT&CK technique was executed without affecting system stability.

The simulation demonstrated how attackers often begin post-compromise activities by collecting detailed information about the compromised host. Although these commands appear benign, they represent a critical stage in the attack lifecycle and should be monitored by defensive security solutions.

---

# Phase Summary

This phase successfully established a functional adversary emulation laboratory capable of executing ATT&CK-mapped Atomic Red Team tests. The environment is now ready for subsequent phases involving multiple technique simulations, ATT&CK mapping, threat modeling, and defensive analysis.