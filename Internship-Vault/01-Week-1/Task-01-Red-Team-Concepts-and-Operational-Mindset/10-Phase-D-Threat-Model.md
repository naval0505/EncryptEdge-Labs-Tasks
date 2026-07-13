# Phase D – Threat Modeling

## Objective

Develop a threat model for a fictional organization by identifying critical assets, realistic threats, and evaluating business risk.

---

# Company Profile -> PayMent Processors

## Company Name -> SecurePay Technologies

## Industry -> Financial Technology (FinTech)

## Employees -> 250

## Description -> SecurePay Technologies is a FinTech company that develops cloud-based payment solutions for businesses. The company manages customer payment information, internal administrative systems, APIs, cloud infrastructure, and financial transactions. Because it processes sensitive financial data, maintaining confidentiality, integrity, and availability is essential for business operations and regulatory compliance.

---

# Critical Assets 

|Asset|Description|Importance|
|---|---|---|
|Customer Database|Stores customer records and payment information|Critical|
|API Gateway|Handles authentication and payment requests|Critical|
|Admin Portal|Administrative management interface|High|

---

# Threat Identification

| Asset             | Threat              | Attack Vector              | Likelihood | Impact | Risk     |
| ----------------- | ------------------- | -------------------------- | ---------- | ------ | -------- |
| Asset             | Threat              | Attack Vector              | Likelihood | Impact | Risk     |
| Customer Database | SQL Injection       | Vulnerable web application | Medium     | High   | High     |
| API Gateway       | Credential Stuffing | Stolen credentials         | High       | High   | Critical |
| Admin Portal      | Phishing            | Social Engineering         | Medium     | High   | High     |

---

# Risk Matrix

|Impact \ Likelihood|Low|Medium|High|
|---|---|---|---|
|High|Medium|High|Critical|
|Medium|Low|Medium|High|
|Low|Low|Low|Medium|

---

# Security Recommendations

- Implement Multi-Factor Authentication (MFA).
- Conduct regular penetration testing and red team exercises.
- Apply secure coding practices and input validation.
- Deploy a Web Application Firewall (WAF).
- Monitor logs with a SIEM for suspicious authentication attempts.
- Enforce least-privilege access control.
- Conduct regular phishing awareness training.
- Perform periodic vulnerability assessments and patch management.

---

# Lessons Learned

- Threat modeling helps identify business-critical risks before they are exploited.
- Risk prioritization allows organizations to focus resources effectively.
- Understanding attacker objectives improves defensive planning.
- Business context is as important as technical vulnerabilities.
- Risk assessments should be reviewed regularly as the environment changes.