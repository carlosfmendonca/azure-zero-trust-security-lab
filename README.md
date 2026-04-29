# Azure Zero Trust Security Lab

## 🔐 Overview
This project simulates a real-world cloud security environment using Microsoft Azure, focusing on identity-based security and Zero Trust principles.

## 🎯 Objective
Design a secure cloud architecture where:
- Identity is the primary control plane
- Access is continuously validated
- Threats are detected in real time

## 🧱 Architecture
The environment includes:
- Microsoft Entra ID (IAM)
- Azure Virtual Machine (target resource)
- Microsoft Sentinel (SIEM)
- Defender for Cloud

## 🔄 Security Flow
1. User authentication via Entra ID (MFA enforced)
2. Conditional Access policies applied
3. Access to Azure resource granted
4. Logs collected and sent to Sentinel
5. Detection of suspicious activity using KQL

## 🔍 Detection Use Case
Simulated brute-force attack detection using:

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by Account, bin(TimeGenerated, 5m)
| where FailedAttempts > 5


---

## 🟡 2. Falta “prova visual” (IMPORTANTE)

👉 Seu diagrama está lá (bom)

Mas faltam prints de:

- Sentinel  
- alerta  
- logs  

---

### 💡 Faça isso:

Adicione pasta:

```plaintext
screenshots/

## 💼 Business Impact
This approach reduces risk of unauthorized access and improves visibility of threats in cloud environments.
