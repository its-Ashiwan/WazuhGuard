# 🏗️ Architecture Overview

This project implements a **Security Operations Center (SOC) detection pipeline** where simulated cyber attacks are generated, monitored, analyzed, and responded to using the Wazuh SIEM stack.

The architecture demonstrates an end-to-end workflow from **attack simulation → log collection → detection → analysis → incident response**.

---

## 🖼️ Architecture Diagram

<img width="864" height="1821" alt="ChatGPT Image Apr 29, 2026, 01_52_30 PM" src="https://github.com/user-attachments/assets/0381059b-e7f8-42d7-913c-0abe711b4ad2" />

---

## 🔴 1. Attack Layer

The attack layer represents the adversary simulation environment. A Kali Linux machine is used to generate controlled attack traffic against the target system.

### 🔹 Attack Scenarios
- 🔍 Nmap Reconnaissance Scan  
- 🔐 Hydra SSH Brute-Force Attack  
- 💻 PowerShell Post-Exploitation Simulation  

These attacks help generate realistic security events for detection and analysis.

---

## 🌐 2. Network Boundary / Internet

This layer represents the communication channel between the attacker and the target system.

- Simulates real-world network exposure  
- Acts as the entry point for malicious traffic  
- Helps visualize attack flow across systems  

---

## 🔵 3. Target System

The target system is a Windows 11 virtual machine acting as the victim endpoint.

### 📊 Data Sources
- 🪟 Windows Security Event Logs  
- 🔑 Authentication Logs  
- ⚙️ Sysmon Telemetry  
- 🧠 Process Execution Events  
- 🌍 Network Connection Logs  

These logs form the **core evidence** for threat detection.

---

## 🟡 4. Log Collection Layer

The Wazuh Agent is installed on the Windows machine to collect and forward logs.

### ⚙️ Responsibilities
- 📥 Collect system and security logs  
- 🔍 Monitor endpoint activity  
- 📤 Forward logs to SIEM  
- 🛰️ Send telemetry for analysis  

---

## 🟠 5. SIEM Engine

The SIEM layer processes, analyzes, and correlates incoming logs.

### 🧩 Components

#### 🛠️ Wazuh Manager
- Rule matching and log analysis  
- Alert generation  
- Event correlation  

#### 📦 Wazuh Indexer (OpenSearch)
- Stores and indexes alerts  
- Enables fast searching and querying  

---

## 🟢 6. Visualization Layer

The Wazuh Dashboard provides a graphical interface for monitoring and analysis.

### 📈 Key Insights
- ⏱️ Alerts over time  
- 🚨 Alert severity distribution  
- 🆔 Top Rule IDs  
- ⚔️ Attack patterns  
- 🌍 Source & destination systems  
- 📜 Raw logs for investigation  

---

## 🟣 7. Security Operations

The SOC Analyst investigates alerts and performs incident analysis.

### 👨‍💻 Responsibilities
- 🧪 Alert triage  
- 🔎 Log investigation  
- 🔗 Event correlation  
- 🧾 Incident documentation  
- ⚠️ Threat classification  

---

## 🛡️ 8. Incident Response & Mitigation

After detection and analysis, mitigation actions are applied to secure the system.

### 🔐 Example Actions
- 🚫 Blocking attacker IPs  
- 🔑 Enforcing strong password policies  
- ❌ Disabling vulnerable services  
- 🧱 System hardening  
- 🧠 Creating custom detection rules  

---

## 🔁 9. Feedback Loop

A continuous improvement cycle is maintained:

➡️ Detection → Analysis → Response → Security Enhancement  

This ensures the system becomes more resilient over time.

---

## 🔄 10. End-to-End Data Flow

1. 🔴 Attacker launches simulated attacks  
2. 🔵 Target system generates logs  
3. 🟡 Wazuh Agent collects telemetry  
4. 🟠 SIEM Engine analyzes events  
5. 🟢 Dashboard visualizes alerts  
6. 🟣 SOC Analyst investigates incidents  
7. 🛡️ Response actions are applied  

---

## 🎯 11. Purpose of the Architecture

This architecture demonstrates:

- ✅ Real-world SOC workflow  
- ✅ Hands-on SIEM implementation  
- ✅ Attack detection & log analysis  
- ✅ Incident response lifecycle  

It showcases practical skills required for **SOC Analyst (L1) and Cybersecurity Intern roles**.
