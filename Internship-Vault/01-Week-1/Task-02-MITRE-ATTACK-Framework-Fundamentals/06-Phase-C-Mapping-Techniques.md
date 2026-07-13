# Phase C – Core Execution: Mapping Techniques

## Objective

The objective of this phase was to execute and analyze MITRE ATT&CK techniques using the Atomic Red Team framework, observe their behavior in a controlled lab environment, and map each activity to its corresponding ATT&CK tactic and technique.

This process helps Red Team operators understand how adversary behaviors translate into practical attack simulations while providing defenders with valuable detection and mitigation opportunities.

---

# Technique Selection

The following ATT&CK techniques were selected based on their relevance to common attack scenarios and the internship objectives.

| ATT&CK ID | Technique | ATT&CK Tactic |
|-----------|-----------|---------------|
| T1082 | System Information Discovery | Discovery |
| T1059 | Command and Scripting Interpreter | Execution |
| T1566 | Phishing | Initial Access |

---

# Technique 1 – T1082: System Information Discovery

## Description

System Information Discovery is a post-compromise technique used by attackers to collect information about the operating system, hardware, and system configuration.

The collected information assists attackers in identifying:

- Operating system version
- System architecture
- Installed software
- Hardware configuration
- Potential privilege escalation opportunities

---

## ATT&CK Mapping

| Property | Value |
|----------|-------|
| Technique ID | T1082 |
| Technique | System Information Discovery |
| Tactic | Discovery |

---

## Atomic Red Team Execution

The Atomic Red Team test for **T1082** was executed in the isolated lab environment.

The test simulated normal system enumeration activities using native Windows commands.

Observed behavior included:

- Querying operating system details
- Reading computer information
- Enumerating hardware information
- Displaying hostname
- Collecting environment details

---

## Expected Result

The execution generated system information without modifying the operating system.

No persistence mechanisms or malicious payloads were introduced during testing.

---

## Detection Opportunities

Security teams can detect this activity by monitoring:

- PowerShell execution logs
- Command Prompt activity
- Windows Event Logs
- Sysmon Process Creation Events
- Endpoint Detection and Response (EDR) alerts

---

## Mitigation

Recommended defensive controls include:

- Enable PowerShell logging
- Monitor abnormal enumeration commands
- Restrict unnecessary administrative privileges
- Deploy Endpoint Detection and Response (EDR)
- Configure SIEM alerting for discovery activity

---

## Evidence

> **Insert screenshot of successful T1082 Atomic Red Team execution.**

---

# Technique 2 – T1059: Command and Scripting Interpreter

## Description

The Command and Scripting Interpreter technique allows attackers to execute commands through scripting languages or command-line interpreters such as:

- PowerShell
- CMD
- Bash
- Python

Threat actors commonly abuse this technique to automate malicious actions after gaining access to a system.

---

## ATT&CK Mapping

| Property | Value |
|----------|-------|
| Technique ID | T1059 |
| Technique | Command and Scripting Interpreter |
| Tactic | Execution |

---

## Typical Adversary Behavior

Attackers may use scripting interpreters to:

- Execute malware
- Download payloads
- Modify system configurations
- Execute reconnaissance commands
- Launch persistence mechanisms

---

## Detection Opportunities

Monitor:

- PowerShell Script Block Logging
- Suspicious command-line arguments
- Parent-child process relationships
- Encoded PowerShell commands
- Abnormal script execution

---

## Mitigation

- Enable PowerShell Constrained Language Mode
- Restrict script execution policies
- Use Microsoft Defender Attack Surface Reduction rules
- Monitor unusual scripting activity
- Apply application whitelisting

---

# Technique 3 – T1566: Phishing

## Description

Phishing remains one of the most common initial access techniques used by threat actors.

The attacker attempts to trick users into:

- Opening malicious attachments
- Visiting malicious websites
- Entering credentials
- Executing malware

---

## ATT&CK Mapping

| Property | Value |
|----------|-------|
| Technique ID | T1566 |
| Technique | Phishing |
| Tactic | Initial Access |

---

## Typical Attack Flow

1. Delivery of phishing email
2. User interaction
3. Payload execution
4. Initial system compromise
5. Command and Control communication

---

## Detection Opportunities

Organizations should monitor:

- Email gateway alerts
- Suspicious attachments
- URL reputation
- User login anomalies
- Endpoint malware detections

---

## Mitigation

- Security awareness training
- Multi-Factor Authentication (MFA)
- Email filtering
- Attachment sandboxing
- URL filtering
- Anti-phishing solutions

---

# ATT&CK Technique Mapping Summary

| Technique | ATT&CK ID | Tactic | Detection Priority |
|-----------|-----------|---------|--------------------|
| System Information Discovery | T1082 | Discovery | Medium |
| Command & Scripting Interpreter | T1059 | Execution | High |
| Phishing | T1566 | Initial Access | Critical |

---

# Observations

The Atomic Red Team framework provides an effective mechanism for safely reproducing adversary behavior within a controlled environment.

During this phase, the mapping process demonstrated that individual techniques rarely occur in isolation. Instead, attackers combine multiple ATT&CK techniques throughout different stages of the intrusion lifecycle.

Understanding these relationships allows security teams to:

- Improve threat hunting
- Enhance detection engineering
- Validate defensive controls
- Conduct realistic adversary emulation
- Prioritize security monitoring

---

# Evidence

### Screenshot 1

> Atomic Red Team execution for T1082.

---

### Screenshot 2

> Updated MITRE ATT&CK Navigator layer highlighting mapped techniques.

---

### Screenshot 3

> Command output generated during Atomic Red Team testing.

---

# Phase Summary

This phase demonstrated how MITRE ATT&CK techniques can be mapped to practical adversary simulations using Atomic Red Team. By correlating executed techniques with ATT&CK tactics, it becomes easier to understand attacker objectives, identify defensive gaps, and improve organizational detection capabilities.

The successful completion of this phase provides the technical foundation required for developing a structured threat model and risk assessment in the following phase.