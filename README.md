# Azure Zero Trust Security Lab
> Hands-on project focused on identity-based security and threat detection in Azure cloud environments.

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
