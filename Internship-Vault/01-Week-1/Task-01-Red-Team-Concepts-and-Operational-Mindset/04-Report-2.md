# Report 2 – Mattermost Privilege Escalation

## Basic Information

Company: Mattermost

Report ID: #1114617

Reported By: fuzzsqlb0f

Date: March 2, 2021

Weakness: Privilege Escalation

Severity: Low (CVSS 2.6)

Status: Resolved

---

## Executive Summary

A privilege escalation vulnerability was discovered in Mattermost where a legitimate channel member could continue posting messages even after the administrator revoked their posting permissions. The attacker captured a previously authorized HTTP request and replayed it after permissions had been removed. Due to insufficient server-side authorization validation, the application accepted the request and published the message. Although the issue did not allow administrative access, it violated the application's authorization model and demonstrated a business logic flaw that could be abused by malicious insiders.

---

## Attack Scenario

### Initial Access

The attacker begins as a legitimate authenticated user who is already a member of a public Mattermost channel.

### Target

The target was Mattermost Cloud.

### Objective

The objective was to bypass channel posting restrictions and continue interacting with a channel despite having posting privileges revoked.

### Attack Goal

The attacker abused an existing session together with a previously captured HTTP request to bypass authorization checks and perform actions that should no longer have been permitted.

---

## Root Cause

### Why was this vulnerability possible?

The server failed to perform proper authorization validation when processing a previously captured request. It trusted an earlier authorized request instead of validating the user's current permissions.

### Was authentication missing?

No.

The attacker was a legitimate authenticated user throughout the attack.

### Was authorization missing?

Yes.

The application failed to verify whether the authenticated user still possessed permission to post in the target channel.

### Was access control incorrectly implemented?

Yes.

Authorization was enforced through the user interface but not consistently validated on the backend API.

---

## Attack Flow

1. User joins a public Mattermost channel.
2. User is granted permission to post messages.
3. User posts a message while capturing the HTTP request using Burp Suite.
4. Administrator revokes the user's posting permission.
5. User attempts to post normally and receives a "Read Only" error.
6. The attacker replays the previously captured request.
7. The server processes the request successfully despite the permission change.
8. Unauthorized message appears in the restricted channel.

---

## Security Impact

### Confidentiality

No direct impact.

### Integrity

High impact.

Unauthorized users can modify channel conversations and post information without permission.

### Availability

No direct availability impact.

### Business Impact

- Bypass of organizational communication policies.
- Potential insider misuse.
- Loss of trust in access control mechanisms.
- Compliance violations in regulated environments.
- Audit logs become less reliable because unauthorized actions appear legitimate.

---

## MITRE ATT&CK Mapping

### Technique

T1078 – Valid Accounts

### Why it applies

The attacker did not compromise credentials or exploit software memory corruption. Instead, they abused a legitimate account whose permissions were not properly validated after authorization changes. The attack relied entirely on misuse of valid credentials and flawed access control.

---

## Cyber Kill Chain

### Reconnaissance 

The attacker identified how channel permissions and posting requests were handled.

---

### Weaponization

Not Applicable.

No payload or malware was created.

---

### Delivery 

Not Applicable.

No malicious payload was delivered.

---

### Exploitation 

The attacker replayed a previously captured HTTP request after posting permissions had been revoked.

The server accepted the request because it failed to revalidate authorization.

---

### Installation 

Not Applicable.

No persistence or malware installation occurred.

---

### Command & Control 
Not Applicable.

No remote control channel was established.

---

### Actions on Objectives

The attacker successfully posted messages in a restricted channel despite no longer having permission to do so.

---

## Defender Perspective

### How could defenders detect this?

- Monitor requests made immediately after permission changes.
- Detect successful API requests that should have been rejected.
- Correlate authorization changes with subsequent user activity.
- Alert on replayed HTTP requests or unusual request patterns.

### Useful Logs

- Authentication logs
- Authorization decision logs
- API audit logs
- Channel permission modification logs
- Web server access logs

### Recommended Security Controls

- Perform server-side authorization validation on every request.
- Never trust cached or previously authorized requests.
- Invalidate permission caches immediately after access changes.
- Implement centralized access control middleware.
- Perform continuous authorization checks throughout the session.

---

## Lessons Learned

- Authorization checks must always occur on the server side.
- User interface restrictions should never be considered a security control.
- Permission changes should immediately affect active sessions.
- Every sensitive API request should validate current user privileges.
- Business logic flaws can be as dangerous as technical vulnerabilities.