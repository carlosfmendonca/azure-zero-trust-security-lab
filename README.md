# Azure Zero Trust Security Lab

> Identity-based threats are one of the primary attack vectors in cloud environments, and this project demonstrates how to detect and mitigate them using Azure security tools.

> Hands-on project simulating a real-world Cloud Security environment using Zero Trust principles, identity-based access control, and threat detection with Microsoft Sentinel.
> Defender for Cloud alerts are integrated into Microsoft Sentinel to provide centralized visibility and correlation of security events.

## 🔐 Overview
This project simulates a real-world Cloud Security environment using Microsoft Azure, focusing on identity-based security, Zero Trust principles, and threat detection.

The lab demonstrates how modern security architectures rely on identity as the primary control plane instead of traditional network perimeters.

---

## 🎯 Objective
Build a secure cloud environment capable of:

- Enforcing identity-based access control
- Detecting suspicious activity in real time
- Reducing risk of unauthorized access
- Applying Zero Trust principles in practice

---

## 🚨 Threat Scenario

This lab simulates a brute-force attack scenario where multiple failed login attempts are generated against an Azure environment.

The goal is to:
- Detect abnormal authentication behavior
- Identify potential credential attacks
- Trigger alerts for investigation

This reflects common real-world attack patterns in cloud environments.

---

## 🧱 Architecture
The environment includes:

- **Microsoft Entra ID (IAM)** → Identity and access control (MFA, Conditional Access)
- **Azure Virtual Machine** → Target resource
- **Microsoft Sentinel (SIEM)** → Log collection and threat detection
- **Defender for Cloud** → Security posture management

---

## 🔄 Security Flow

1. User attempts authentication via Entra ID
2. Conditional Access policies validate access (MFA enforced)
3. Access is granted to Azure resources
4. Security logs are generated and sent to Microsoft Sentinel
5. Sentinel analyzes events and detects suspicious behavior
6. Alerts are triggered for investigation

---

## 🔍 Detection Use Case — Brute Force Attack

This lab simulates multiple failed login attempts and detects abnormal behavior using KQL:

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by Account, bin(TimeGenerated, 5m)
| where FailedAttempts > 5

---

## 🔎 Investigation

Detected events can be correlated with identity logs and enriched with additional context to support incident investigation and response.

---

## 🏦 Fintech Security Context

In financial environments, identity-based attacks are one of the main vectors for unauthorized access.

This lab demonstrates how:
- Identity becomes the primary security layer
- Continuous monitoring is required
- SIEM solutions provide visibility and response capability

---

## ⚙️ Security Controls Implemented

- Multi-Factor Authentication (MFA)
- Conditional Access policies
- Log collection and centralization
- Real-time detection with KQL
- Security monitoring with SIEM (Sentinel)

---

## 📊 Security Operations Perspective

This lab simulates a simplified SOC workflow:
- Log ingestion
- Detection
- Alerting
- Investigation

Providing a practical view of cloud security operations.

---

## ⚡ Response

Potential response actions include:
- Account lockout after multiple failed attempts
- Conditional Access policy enforcement
- Alert escalation for investigation

---

## 🎯 MITRE ATT&CK Mapping

- Technique: T1110 (Brute Force)
- Tactic: Credential Access

This lab simulates detection of credential-based attacks aligned with MITRE ATT&CK framework.

This architecture follows an identity-first security model, where access decisions are based on user context rather than network location.



