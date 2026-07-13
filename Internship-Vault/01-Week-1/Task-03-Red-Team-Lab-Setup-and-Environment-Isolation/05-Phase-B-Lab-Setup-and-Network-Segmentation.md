
# Phase B – Lab Setup & Network Segmentation

## Objective

The objective of this phase was to configure an isolated Red Team laboratory using VMware Workstation and Kali Linux, establish secure network segmentation, and validate communication with a vulnerable target machine in a controlled environment.

Rather than deploying Metasploitable2, an intentionally vulnerable HackMyVM target was used to validate the laboratory configuration and offensive security workflow.

---

# Laboratory Environment

| Component | Details |
|-----------|---------|
| Hypervisor | VMware Workstation |
| Attacker Machine | Kali Linux |
| Target Machine | HackMyVM Vulnerable Machine |
| Network Type | Isolated Virtual Network |
| Monitoring Tool | Wireshark |
| Reconnaissance Tool | Nmap |

---

# Environment Preparation

The laboratory was prepared by configuring virtual machines within VMware Workstation.

The following preparation steps were completed:

- Installed Kali Linux.
- Imported the HackMyVM target machine.
- Verified virtual network configuration.
- Confirmed communication between attacker and target.
- Prepared the environment for reconnaissance and exploitation exercises.

---

# Network Segmentation

To maintain laboratory isolation, both virtual machines were connected through VMware's isolated virtual networking.

Isolation ensures:

- Offensive traffic remains within the lab.
- External devices are protected.
- Vulnerable systems cannot communicate with production networks.
- Testing remains compliant with ethical hacking practices.

---

# Connectivity Verification

Connectivity between the attacker and target machine was confirmed before beginning reconnaissance activities.

Verification included:

- IP address assignment
- Network adapter verification
- Basic connectivity testing
- Virtual network communication

Successful communication confirmed that the laboratory was functioning correctly.

---

# Reconnaissance Preparation

After verifying connectivity, the target machine was prepared for enumeration using standard reconnaissance techniques.

The laboratory environment supported:

- Network discovery
- Port scanning
- Service enumeration
- Vulnerability identification

These activities simulate the initial stages of a real-world penetration test.

---

# Operational Benefits

Using an isolated virtual laboratory provides several advantages:

- Safe offensive testing
- Controlled experimentation
- Repeatable exercises
- Snapshot recovery
- Ethical penetration testing
- Reduced operational risk

---

# Evidence

### Screenshot 1 – VMware Virtual Machine Configuration

> *Insert screenshot from one of your HackMyVM VMware machine settings.*

---

### Screenshot 2 – Nmap Scan

> *Insert the Nmap scan screenshot from your completed HackMyVM write-up.*

---

### Screenshot 3 – Target Machine Access

> *Insert the HackMyVM login screen, shell access, or exploitation evidence from your previous machine.*

---

# Observations

The laboratory successfully demonstrated the principles of Red Team environment preparation and network segmentation. Although the original task referenced Metasploitable2, the same learning objectives were achieved using a HackMyVM vulnerable machine hosted within the isolated VMware environment.

This approach provided practical experience with virtual networking, reconnaissance, and offensive security workflows while maintaining a secure and controlled testing environment.

---

# Phase Summary

This phase established a secure Red Team laboratory capable of supporting penetration testing activities. VMware virtualization, isolated networking, and a vulnerable HackMyVM target provided a realistic environment for validating communication, performing reconnaissance, and preparing for future adversary emulation exercises.