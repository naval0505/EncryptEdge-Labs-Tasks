# Phase C – Adversarial Analysis

## Objective

Analyze a real-world HackerOne report by mapping attacker behavior to the Cyber Kill Chain and MITRE ATT&CK framework.

---

# Selected Report

**Company:** HackerOne

**Report ID:** #262661

**Report Link:** https://hackerone.com/reports/262661

**Weakness:** Insecure Direct Object Reference (IDOR)

**Severity:** Low (3.4)

**Status:** Resolved

### Reason for Selection

This report was selected because it demonstrates a real-world Insecure Direct Object Reference (IDOR) vulnerability involving improper authorization validation. Although classified as a low-severity issue, it illustrates how manipulating object references within authenticated requests can bypass business logic, impact user reputation, and expose unauthorized information. IDOR remains one of the most common web application vulnerabilities identified during penetration tests and red team engagements.

---

# Attack Overview

The vulnerability existed within HackerOne's Hacker Review functionality.

When a security team member submitted feedback for a hacker, the application generated a POST request containing several parameters, including the username of the hacker receiving the review.

The attacker intercepted the HTTP request using an interception proxy such as Burp Suite and modified the `hacker_username` parameter before forwarding the request to the server.

Because the backend failed to verify that the supplied username actually belonged to the report being reviewed, the application accepted the manipulated request and assigned feedback to another participant.

As a result, an attacker could:

- Create unauthorized public reviews.
- Modify another hacker's public reputation.
- Trigger email notifications to unintended users.
- Disclose report titles and private feedback.
- Abuse the review system without directly interacting with the victim's report.

Although HackerOne ultimately classified the issue as Low severity due to additional authorization conditions, the report demonstrates a classic authorization weakness and business logic flaw.

---

# Cyber Kill Chain Mapping

## 1. Reconnaissance 

The attacker explored the Hacker Review functionality and analyzed how feedback requests were processed.

Activities included:

- Understanding the review workflow.
- Observing request parameters.
- Identifying the `hacker_username` parameter.
- Studying application logic.

---

## 2. Weaponization 

Not Applicable.

The attack did not require malware, exploits, payload generation, or malicious binaries.

---

## 3. Delivery 

Not Applicable.

No malicious payload was delivered to another system.

The attacker only replayed a modified HTTP request.

---

## 4. Exploitation 

The attacker captured the legitimate POST request using Burp Suite.

The following parameter was modified:

```
hacker_username=<victim_username>
```

After forwarding the modified request, the server failed to verify ownership of the report and accepted the manipulated request.

This represents the primary exploitation phase.

---

## 5. Installation 

Not Applicable.

No persistence mechanism, malware, or backdoor was installed.

---

## 6. Command & Control (C2) 

Not Applicable.

No compromised system communicated with an attacker-controlled server.

---

## 7. Actions on Objectives 

The attacker successfully achieved their objective by:

- Creating unauthorized public reviews.
- Modifying another hacker's profile reputation.
- Triggering email notifications to unintended recipients.
- Accessing report-related information.
- Demonstrating a business logic flaw in the review system.

---

# MITRE ATT&CK Mapping

| Technique | ID | Reason |
|-----------|----|--------|
| Valid Accounts | T1078 | The attacker used a legitimate HackerOne account throughout the attack. |
| Exploit Public-Facing Application | T1190 | The vulnerability existed within a publicly accessible web application endpoint that processed attacker-controlled parameters. |

---

# Maltego Analysis

## Entities Identified

- hackerone.com
- Hacker Review Endpoint
- Victim User
- Attacker Account
- HTTP POST Request
- Review System

---

## Relationships

Attacker Account

↓

Authenticated Session

↓

Captured POST Request

↓

Modified `hacker_username`

↓

Unauthorized Review

↓

Victim Profile

↓

Reputation Manipulation

---

## Infrastructure Observed

The analysis identified the HackerOne web application along with the review endpoint responsible for processing user feedback.

The attack relied entirely on manipulation of application logic rather than infrastructure weaknesses.

---

# Detection Opportunities

A Security Operations Center (SOC) could detect this attack by monitoring:

- Review requests where the report owner and review recipient differ.
- Sudden reputation changes affecting unrelated users.
- Multiple review submissions from a single account.
- Parameter tampering involving `hacker_username`.
- Unexpected email notifications generated by review actions.
- Authorization failures recorded by backend services.

---

# Defensive Recommendations

- Perform server-side authorization validation on every request.
- Never trust user-supplied object identifiers.
- Validate that the reviewed user owns the referenced report.
- Implement object-level authorization checks (BOLA).
- Log all review modifications for auditing.
- Generate alerts when review recipients differ from report owners.
- Perform secure code reviews focusing on business logic vulnerabilities.

---

# Lessons Learned

- IDOR vulnerabilities often result from missing object-level authorization rather than authentication failures.
- Every user-controlled parameter should be validated against server-side ownership checks.
- Business logic vulnerabilities can directly impact user trust and application integrity.
- Backend authorization must always be enforced, regardless of client-side restrictions.
- Red Team operators should analyze application workflows rather than focusing solely on technical exploits.
- Understanding trust relationships between users and application objects is critical during offensive security assessments.


# Attack Diagrams

                           hackerone.com
                               │
                               ▼
                    Hacker Review Feature
                               │
                               ▼
                    POST /hacker_reviews
                               │
                               ▼
                  hacker_username Parameter
                               │
                    (Modified by attacker)
                               │
                               ▼
          Broken Object Level Authorization (IDOR)
                               │
                ┌──────────────┴──────────────┐
                │                             │
                ▼                             ▼
      Victim Profile                 Private Feedback
                │                             │
                └──────────────┬──────────────┘
                               ▼
                    Reputation Manipulation

![[q7.png]]

