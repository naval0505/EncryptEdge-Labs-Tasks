
# Phase D – Independent Extension: Threat Modeling

## Objective

The objective of this phase was to develop a structured threat model for a fictional organization by identifying critical business assets, evaluating realistic cyber threats, assessing potential business risks, and recommending security controls aligned with the NIST Cybersecurity Framework.

Threat modeling enables organizations to proactively identify weaknesses before they can be exploited by adversaries and supports both offensive and defensive security planning.

---

# Organization Profile

| Property       | Details                                            |
| -------------- | -------------------------------------------------- |
| Company Name   | TridentPay Technologies                            |
| Industry       | Financial Technology (FinTech)                     |
| Employees      | 250                                                |
| Business Type  | Payment Processing Services                        |
| Environment    | Hybrid Cloud Infrastructure                        |
| Security Focus | Customer Payment Security & Financial Transactions |

---

# Company Overview

SecurePay Technologies is a medium-sized financial technology company that develops secure payment processing solutions for online merchants and enterprise clients.

The organization processes thousands of financial transactions daily while storing sensitive customer information, payment records, authentication data, and internal business documentation. Due to the nature of its services, SecurePay Technologies is an attractive target for cybercriminals seeking financial gain, sensitive customer information, or disruption of business operations.

Maintaining the confidentiality, integrity, and availability of business assets is critical for regulatory compliance, customer trust, and operational continuity.

---

# Critical Business Assets

The following assets were identified as the most valuable resources within the organization.

| Asset | Importance | Reason |
|--------|------------|--------|
| Customer Payment Database | Critical | Stores customer payment records and sensitive financial data |
| Internal Application Servers | High | Hosts payment processing applications and APIs |
| Employee Workstations | High | Daily operational systems used by staff |
| Authentication Infrastructure | Critical | Controls access to internal resources |
| Cloud Storage | High | Stores business documents and backups |

---

# Threat Actors

Several threat actors may target SecurePay Technologies.

| Threat Actor | Motivation |
|--------------|------------|
| Cybercriminal Groups | Financial gain |
| Ransomware Operators | Extortion |
| Insider Threats | Data theft or sabotage |
| Advanced Persistent Threats (APT) | Long-term espionage |
| Phishing Campaign Operators | Credential theft |

---

# Potential Attack Vectors

The following attack vectors were identified during the threat assessment.

| Attack Vector | Related ATT&CK Technique |
|---------------|--------------------------|
| Phishing Emails | T1566 |
| Stolen Credentials | T1078 |
| Command Execution | T1059 |
| System Discovery | T1082 |
| Obfuscated Files | T1027 |

These techniques align with the ATT&CK mappings analyzed during the previous phase.

---

# Risk Assessment Matrix

The identified risks were evaluated based on their likelihood of occurrence and potential business impact.

| Threat | Likelihood | Impact | Overall Risk |
|---------|------------|--------|--------------|
| Phishing Campaign | High | High | Critical |
| Credential Theft | High | High | Critical |
| Ransomware Attack | Medium | Critical | High |
| Insider Data Theft | Medium | High | High |
| System Discovery | High | Medium | Medium |
| Malware Execution | Medium | High | High |

---

# Business Impact Analysis

Successful exploitation of these threats could result in:

- Financial losses
- Regulatory penalties
- Customer data exposure
- Payment service disruption
- Loss of customer trust
- Operational downtime
- Reputation damage

---

# Threat Modeling Diagram

```
                    Internet
                        │
                        ▼
              ┌──────────────────┐
              │   Phishing Email │
              └────────┬─────────┘
                       │
                       ▼
             Employee Workstation
                       │
                       ▼
          Stolen Credentials (T1078)
                       │
                       ▼
      Command Execution (T1059)
                       │
                       ▼
 System Information Discovery (T1082)
                       │
                       ▼
     Payment Processing Servers
                       │
                       ▼
 Customer Payment Database
```

---

# Recommended Security Controls

The following mitigations are aligned with the NIST Cybersecurity Framework.

## Identify

- Maintain an accurate inventory of business assets.
- Classify sensitive financial information.
- Perform regular risk assessments.

---

## Protect

- Enforce Multi-Factor Authentication (MFA).
- Implement least privilege access.
- Encrypt sensitive customer data.
- Apply secure password policies.
- Conduct employee phishing awareness training.

---

## Detect

- Deploy Endpoint Detection and Response (EDR).
- Monitor PowerShell and command-line activity.
- Centralize logs within a SIEM platform.
- Enable continuous network monitoring.
- Detect abnormal authentication attempts.

---

## Respond

- Maintain an incident response plan.
- Isolate compromised systems immediately.
- Investigate suspicious activity.
- Notify stakeholders when required.

---

## Recover

- Maintain tested offline backups.
- Regularly validate disaster recovery procedures.
- Restore critical services using documented recovery plans.

---

# MITRE ATT&CK Mapping

| ATT&CK Technique | Business Risk |
|------------------|---------------|
| T1566 – Phishing | Initial compromise |
| T1078 – Valid Accounts | Unauthorized access |
| T1059 – Command and Scripting Interpreter | Malware execution |
| T1082 – System Information Discovery | Internal reconnaissance |
| T1027 – Obfuscated Files | Defense evasion |

---

# Observations

The threat model demonstrates how multiple ATT&CK techniques can be chained together during a real-world attack. Rather than relying on a single exploit, adversaries typically progress through multiple stages of the ATT&CK lifecycle, beginning with initial access and ending with data theft, persistence, or operational disruption.

Understanding these attack paths enables organizations to prioritize security investments, improve detection engineering, and implement layered defensive controls.

---

# Evidence

### Screenshot 1

> ![[q9.png]]

---

### Screenshot 2

> |Impact ↓ / Likelihood →|Low|Medium|High|
|---|---|---|---|
|Critical|||🔴 Phishing|
|High||🟠 Insider|🔴 Credential Theft|
|Medium||🟡 Discovery||
|Low||||

---

### Screenshot 3

> ![[q10.png]]

---

# Phase Summary

This phase successfully developed a structured threat model for SecurePay Technologies by identifying critical business assets, evaluating realistic cyber threats, mapping adversary behavior to MITRE ATT&CK techniques, and recommending security controls aligned with the NIST Cybersecurity Framework.

The resulting threat model provides a practical foundation for understanding organizational risk, improving defensive strategies, and supporting future adversary emulation exercises.