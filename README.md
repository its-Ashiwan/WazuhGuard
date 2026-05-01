# 🛡️ SIEM-Based Threat Detection & Analysis Lab

## 📌 Overview

This project demonstrates a real-world **Security Operations Center (SOC)** simulation using Wazuh SIEM to perform threat detection, monitoring, and incident analysis.

The lab replicates practical cybersecurity workflows by integrating endpoint telemetry, SIEM-based detection, and attack simulation.

---

## 🎯 Objective

To develop hands-on SOC analyst skills including:

* Log analysis
* Alert investigation
* Event correlation
* Threat detection

---

## 🚀 Key Highlights

* Analyzed **100,000+ security events** over a month
* Detected **Brute Force attacks using Hydra**
* Identified detection gaps in reconnaissance & execution techniques
* Demonstrated real-world SIEM limitations and rule tuning needs

---

## 🏗️ Architecture

```
Kali Linux (Attacker)
        ↓
Windows 11 (Victim + Sysmon + Wazuh Agent)
        ↓
Wazuh Manager (Amazon Linux 2023)
        ↓
Wazuh Dashboard
        ↓
SOC Analysis & Visualization
```

### 📸 Architecture Diagram

<img width="759" height="1600" alt="WhatsApp Image 2026-04-29 at 1 52 44 PM" src="https://github.com/user-attachments/assets/def88e04-0fb6-47c0-a51e-3b7da9fb7107" />


---

## 📊 Dashboard Preview

### 🔹 Wazuh Dashboard Overview

<img width="840" height="519" alt="Alerts By Severity" src="https://github.com/user-attachments/assets/083127b3-7157-4c3e-a074-b7e9a0094a61" />

<img width="855" height="529" alt="High Severity Alerts" src="https://github.com/user-attachments/assets/a7e4e2d2-8bde-4c77-8825-ead6a154a041" />



👉 Shows overall alert monitoring and system activity

---

### 🔹 Alerts Timeline (Spike Detection)

<img width="831" height="468" alt="Alerts Over Time (1)" src="https://github.com/user-attachments/assets/f5795f68-d4b1-4830-b316-c038c68c8428" />


👉 Clear spike observed during brute-force attack

---

## ⚙️ Tech Stack

| Layer               | Technology        |
| ------------------- | ----------------- |
| SIEM                | Wazuh             |
| Endpoint Monitoring | Sysmon            |
| Target System       | Windows 11        |
| Attacker System     | Kali Linux        |
| Server OS           | Amazon Linux 2023 |
| Virtualization      | VMware            |

---

## 🚨 Attack Scenarios

### 🔐 Brute Force Attack (Hydra)

* High-frequency authentication attempts
* Windows Event ID **4625 (Failed Login)**


### 📸 Detection in Wazuh

<img width="853" height="532" alt="Brute Force Attack" src="https://github.com/user-attachments/assets/bf1fb5b6-e5a3-44f9-b264-b0deb216cf11" />


👉 Multiple failed login alerts detected in dashboard

---

## 🔍 Log Analysis

### 📸 Detailed Log View

<img width="1609" height="423" alt="Logs 1" src="https://github.com/user-attachments/assets/337c328e-9316-4f34-9503-5381cf77a625" />

<img width="1609" height="428" alt="Logs 2" src="https://github.com/user-attachments/assets/15dfa936-3f9a-4aa9-9e1d-ea5b816e12a0" />


👉 Shows rule ID, rule Description

---

## 🔍 Key Findings

* Generated **100,000+ logs** during attack simulations
* Clear alert spikes during brute-force activity
* Dominant alert:
  **Logon Failure – Unknown user or bad password**

---

## ⚠️ Detection Limitations

* Limited visibility for reconnaissance techniques
* Low detection for advanced execution activities

👉 Highlights need for rule tuning and detection engineering

---

## 🧠 Event Correlation

```
Multiple Failed Logins (Event ID 4625)
+ High Alert Frequency
+ Same Source IP
↓
Confirmed Brute Force Attack
```

---

## 🧬 MITRE ATT&CK Mapping

| Technique         | ID    |
| ----------------- | ----- |
| Brute Force       | T1110 |
| Command Execution | T1059 |
| Network Discovery | T1046 |

---

## 📂 Project Structure

```
.
├── architecture/
├── setup/
├── attacks/
├── analysis/
├── screenshots/
├── report/
└── README.md
```

---

## 🛠️ Setup (High-Level)

1. Deploy Wazuh OVA
2. Configure Wazuh Manager
3. Install Wazuh Agent
4. Configure Sysmon
5. Execute attacks
6. Monitor alerts

---

## 📄 Detailed Report

📥 **Download Full SOC Report:**  
[Click here to view report](report/SOC_Report.docx)

👉 Contains:

* Complete attack analysis
* Screenshots with explanation
* Detection insights
* SOC findings

---

## 🧩 Challenges

* Limited detection visibility in some attack scenarios
* Sysmon configuration tuning
* Dashboard filtering issues
* VM networking problems

---

## 🚀 Key Learnings

* SIEM effectiveness depends on log quality
* Detection engineering is critical
* Log analysis > tool usage

---

## 🎯 Why This Project Matters

Demonstrates real SOC analyst capabilities:

* Threat detection
* Log correlation
* Detection gap analysis

---

## 📈 Future Improvements

* Custom Wazuh rules
* Threat intelligence integration
* Automated response workflows
* Zeek integration

---

## ⭐ Final Note

This project reflects a complete SOC workflow from detection to analysis.

👉 Built to demonstrate real-world cybersecurity and Blue Team skills

