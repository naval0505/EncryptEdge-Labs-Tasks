
# Phase D – Independent Extension: Threat Modeling

## Objective

The objective of this phase was to identify potential containment failures within the Red Team laboratory, assess their associated risks, and recommend appropriate security controls to maintain a safe and isolated offensive security environment.

Threat modeling helps Red Team operators understand how misconfigurations or operational mistakes can compromise the integrity of a laboratory environment and potentially affect production systems.

---

# Introduction

A Red Team laboratory contains intentionally vulnerable systems and offensive security tools. Without proper isolation and security controls, these environments can become a risk to the host operating system, local network, or even external infrastructure.

This threat model evaluates the virtual lab by identifying critical assets, potential threats, assessing business impact, and recommending mitigation strategies that align with cybersecurity best practices.

---

# Lab Environment Overview

| Property | Details |
|----------|---------|
| Environment | VMware Virtual Lab |
| Attacker Machine | Kali Linux |
| Target Machine | Metasploitable2 (Planned) |
| Network Type | Host-Only Network |
| Host Operating System | Linux |
| Monitoring Tool | Wireshark |

---

# Critical Assets

The following assets were identified as critical components of the Red Team laboratory.

| Asset | Importance | Description |
|--------|------------|-------------|
| Host Operating System | Critical | Primary workstation hosting all virtual machines |
| Kali Linux VM | High | Offensive security workstation used for testing |
| Metasploitable2 VM | High | Intentionally vulnerable target system |
| VMware Virtual Network Adapter | High | Provides isolated communication between VMs |
| Virtual Machine Snapshots | Medium | Enables rollback to a clean testing state |

---

# Threat Identification

The following threats were identified during the assessment.

| Threat | Description |
|---------|-------------|
| Malware Escape | Malicious software escapes the virtual environment and reaches the host system. |
| Misconfigured NAT Adapter | Incorrect network settings expose the lab to external networks. |
| Shared Folder Exposure | Malware or sensitive files transfer between host and guest systems. |
| Snapshot Corruption | Loss or corruption of recovery snapshots prevents restoring a clean environment. |
| Unauthorized Internet Access | Vulnerable systems communicate with external networks during testing. |

---

# Risk Assessment Matrix

| Threat | Likelihood | Impact | Overall Risk |
|---------|------------|--------|--------------|
| Malware Escape | Medium | High | High |
| Misconfigured NAT Adapter | High | High | Critical |
| Shared Folder Exposure | Medium | Medium | Medium |
| Snapshot Corruption | Low | Medium | Low |
| Unauthorized Internet Access | High | High | Critical |

---

# Recommended Mitigations

The following controls are recommended to reduce identified risks.

| Threat | Recommended Mitigation |
|---------|------------------------|
| Malware Escape | Use Host-Only networking, disable shared folders, isolate malware analysis. |
| Misconfigured NAT Adapter | Verify network mode before every engagement and disable unused adapters. |
| Shared Folder Exposure | Disable shared folders, clipboard sharing, and drag-and-drop features. |
| Snapshot Corruption | Create regular snapshots and maintain backup copies of virtual machines. |
| Unauthorized Internet Access | Restrict internet connectivity for vulnerable virtual machines and continuously monitor traffic with Wireshark. |

---

# Risk Matrix

| Impact ↓ / Likelihood → | Low                 | Medium                 | High                                                       |
| ----------------------- | ------------------- | ---------------------- | ---------------------------------------------------------- |
| **High**                |                     | Malware Escape         | Misconfigured NAT Adapter<br> Unauthorized Internet Access |
| **Medium**              | Snapshot Corruption | Shared Folder Exposure |                                                            |
| **Low**                 |                     |                        |                                                            |

---

# Operational Best Practices

To maintain a secure Red Team laboratory, the following practices should be adopted:

- Use Host-Only networking for all offensive security exercises.
- Disable shared folders, clipboard sharing, and drag-and-drop.
- Maintain clean virtual machine snapshots before testing.
- Monitor network traffic using Wireshark.
- Regularly update the attacker virtual machine.
- Avoid connecting intentionally vulnerable systems directly to the internet.

---

# Evidence

### Screenshot 1 – Risk Matrix

|**Impact ↓ / Likelihood →**|**Low**|**Medium**|**High**|
|---|---|---|---|
|**High**||🟠 Malware Escape|🔴 Misconfigured NAT Adapter🔴 Unauthorized Internet Access|
|**Medium**|🟢 Snapshot Corruption|🟡 Shared Folder Exposure||
|**Low**||||

---

### Screenshot 2 – Threat Model Diagram

> ![[q13.png]]

---

### Screenshot 3 – VMware Network Configuration

> ![[q13.png]]

---

# Observations

The threat modeling process highlighted that the security of a Red Team laboratory depends not only on the tools being used but also on the underlying infrastructure and operational discipline.

Simple configuration mistakes, such as enabling NAT networking or shared folders, can significantly increase the risk of compromising the host operating system or exposing vulnerable systems to external networks.

Implementing layered isolation controls helps ensure that offensive security activities remain safe, repeatable, and compliant with ethical testing practices.

---

# Phase Summary

This phase successfully identified critical laboratory assets, evaluated realistic containment risks, and proposed practical mitigation strategies for maintaining a secure Red Team environment.

By applying threat modeling principles, the laboratory design supports safe adversary emulation while minimizing the likelihood of accidental exposure, malware escape, or unauthorized network communication.