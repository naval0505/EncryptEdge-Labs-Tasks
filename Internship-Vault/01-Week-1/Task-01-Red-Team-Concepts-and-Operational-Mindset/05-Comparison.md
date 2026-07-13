# Phase A – Comparison & Analysis

# Comparison Between Vulnerability Assessment, Penetration Testing, and Red Teaming

| Feature          | Vulnerability Assessment                    | Penetration Testing                        | Red Team Engagement                                                          |
| ---------------- | ------------------------------------------- | ------------------------------------------ | ---------------------------------------------------------------------------- |
| Primary Goal     | Identify known vulnerabilities              | Exploit vulnerabilities to verify risk     | Simulate a real-world adversary                                              |
| Focus            | Finding weaknesses                          | Exploiting weaknesses                      | Achieving attacker objectives while remaining stealthy                       |
| Methodology      | Automated scanners with manual verification | Manual testing with exploitation           | Multi-stage adversary emulation using TTPs                                   |
| Scope            | Broad infrastructure assessment             | Specific applications, systems or networks | Entire organization including people, processes and technology               |
| Deliverable      | List of vulnerabilities                     | Technical findings with proof-of-concept   | Executive report describing attack paths, business impact and defensive gaps |
| Stealth Required | No                                          | Limited                                    | Yes                                                                          |
| Objective        | Improve security posture                    | Validate exploitable vulnerabilities       | Measure detection and response capabilities                                  |
| Examples         | Nessus, OpenVAS                             | Burp Suite, Metasploit                     | Cobalt Strike, MITRE ATT&CK, OSINT, Social Engineering                       |

---

# Comparison of the Two HackerOne Reports

| Category            | Report 1 - Automattic (Cloudup)                 | Report 2 - Mattermost                                      |
| ------------------- | ----------------------------------------------- | ---------------------------------------------------------- |
| Weakness            | Improper Authentication / Broken Access Control | Privilege Escalation through Authorization Bypass          |
| Root Cause          | URL manipulation bypassed access validation     | Server failed to revalidate permissions after they changed |
| Initial Access      | Legitimate user account                         | Legitimate user account                                    |
| Attack Method       | Modify the URL by removing `/download`          | Replay a previously captured HTTP request                  |
| Authentication      | User was authenticated                          | User was authenticated                                     |
| Authorization       | Failed                                          | Failed                                                     |
| Business Logic Flaw | Yes                                             | Yes                                                        |
| Confidentiality     | High                                            | Low                                                        |
| Integrity           | Medium                                          | High                                                       |
| Availability        | Low                                             | Low                                                        |
| Business Impact     | Exposure of confidential files                  | Unauthorized posting and policy bypass                     |
| MITRE ATT&CK        | T1619 – Cloud Storage Object Discovery          | T1078 – Valid Accounts                                     |
| Cyber Kill Chain    | Recon → Exploitation → Actions on Objectives    | Recon → Exploitation → Actions on Objectives               |

---

# Authentication vs Authorization

## Authentication

Authentication answers the question:

**Who are you?**

Examples:

- Username and password
- Multi-Factor Authentication (MFA)
- SSO
- OAuth

Authentication verifies the user's identity before granting access to a system.

---

## Authorization

Authorization answers the question:

**What are you allowed to do?**

Examples:

- Read files
- Delete data
- Upload files
- Access admin panels
- Post messages in a channel

Authorization determines which actions an authenticated user is permitted to perform.

---

# Observations from Both Reports

## Similarities

- Both attacks required a legitimate user account.
- Both exploited server-side authorization weaknesses.
- Neither attack required malware or remote code execution.
- Both demonstrated Broken Access Control.
- Both exposed weaknesses in business logic implementation.
- Both could have been prevented through consistent server-side authorization checks.

---

## Differences

### Automattic

- Targeted protected files.
- Resulted in unauthorized information disclosure.
- Exploited predictable URL behavior.

### Mattermost

- Targeted communication permissions.
- Resulted in unauthorized actions rather than data theft.
- Exploited stale authorization after permission changes.

---

# AI Summary

A Vulnerability Assessment identifies known weaknesses without attempting exploitation. Its primary objective is to provide organizations with an inventory of security issues that require remediation.

A Penetration Test goes further by actively exploiting vulnerabilities to determine whether they are practically exploitable and to measure their technical impact.

A Red Team Engagement simulates a realistic attacker attempting to achieve business objectives rather than simply exploiting vulnerabilities. Red teams combine reconnaissance, social engineering, privilege escalation, lateral movement, persistence, and defense evasion techniques while attempting to remain undetected. Their purpose is to evaluate an organization's people, processes, detection capabilities, and incident response under realistic attack conditions.

The two HackerOne reports demonstrate the importance of authorization validation. In both cases, the attackers already possessed legitimate accounts; however, weaknesses in server-side access control allowed them to perform actions beyond their intended privileges. These reports illustrate that effective security depends not only on strong authentication but also on continuous authorization checks and secure business logic implementation.

---

# Lessons Learned

- Authentication alone does not provide security if authorization is improperly implemented.
- Every sensitive request must be validated on the server side.
- Client-side restrictions should never be trusted.
- Business logic vulnerabilities can have severe business consequences.
- Continuous permission validation is essential after privilege changes.
- Red Team operators focus on identifying attack paths rather than isolated vulnerabilities.