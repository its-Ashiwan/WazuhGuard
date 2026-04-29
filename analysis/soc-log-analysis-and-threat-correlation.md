# 🧠 SOC Log Analysis & Threat Correlation

## 📌 Overview

This section provides an in-depth analysis of security logs generated within a simulated **Security Operations Center (SOC)** environment using Wazuh SIEM.

The primary objective is to detect attack patterns, correlate security events, and assess the effectiveness of the SIEM system in identifying real-world threats.

Log sources include:

* Windows endpoint (Sysmon + Wazuh Agent)
* Centralized Wazuh Manager

---

## 📊 Log Ingestion & System Behavior

* Total events processed: **100,000+ logs**
* Monitoring duration: ~1 month
* Continuous and stable log ingestion observed

### 🧠 Key Insight

The system demonstrates a **consistent and reliable log pipeline**, which is critical for any SOC environment.

Notable spikes in log volume were observed during simulated attack phases, clearly distinguishing malicious activity from normal system behavior.
<img width="849" height="532" alt="Screenshot 2026-04-29 122234" src="https://github.com/user-attachments/assets/913bdaae-2f7d-4762-a823-6bbce9cf3f02" />


---

## ⏱️ Temporal Activity Analysis

### Observations:

* Baseline system activity shows **uniform log generation**
* Attack execution results in **sudden, high-volume spikes**
* Brute-force activity generates the **most intense log bursts**

### 🧠 Interpretation:

* Normal activity → predictable and low-variance
* Malicious activity → high deviation from baseline

This variation is a key indicator used in SOC environments for anomaly detection and early threat identification.

---

## 🔐 Authentication Anomaly Detection (Brute Force)

### Observed Indicators:

* Frequent failed login attempts
* Windows Event ID: **4625 (Failed Authentication)**
* Repeated attempts from a single source
* High-speed credential attempts in short intervals

### 🧠 Analysis:

These patterns strongly indicate a **brute-force attack**, where automated tools attempt multiple credential combinations rapidly.
<img width="853" height="532" alt="Screenshot 2026-04-27 100502" src="https://github.com/user-attachments/assets/a778f04e-6d9e-4acf-b3b9-9d9c986a7d30" />


### 📡 Detection Outcome:

* Successfully identified by Wazuh SIEM
* High alert frequency visible in dashboard
* Primary alert classification:

  * *Authentication Failure – Invalid credentials*

### 🎯 SOC Perspective:

Authentication anomalies are high-confidence indicators of attack activity and are effectively captured using standard SIEM rules.

---

## ⚡ Process Monitoring & PowerShell Activity

### Observations:

* Sysmon Event ID: **1 (Process Creation)**
* PowerShell execution detected
* Low frequency (~5–7 events)

### 🧠 Analysis:

* Confirms visibility into process-level activity
* Limited alerting suggests:

  * Basic rule coverage
  * Lack of behavioral detection logic

### 🎯 SOC Insight:

PowerShell is frequently leveraged in advanced attack stages, including:

* Fileless malware execution
* Post-exploitation techniques
* Privilege escalation

Low detection volume highlights the need for **enhanced rule tuning and advanced monitoring strategies**.

---

## 🌐 Reconnaissance Activity (Nmap Scan)

### Observations:

* No significant alerts generated during scan execution
* Lack of clear port scanning detection

### 🧠 Analysis:

* Indicates a **visibility gap** in reconnaissance detection
* Default SIEM rules are insufficient for identifying such activity

### 🎯 SOC Insight:

Reconnaissance is a critical early attack phase and often requires:

* Custom detection rules
* Integration with network monitoring tools (e.g., Zeek, Suricata)

---

## 📊 Dashboard Insights & Alert Correlation

### Observed Patterns:

* Sharp alert spikes during brute-force activity
* Authentication-related alerts dominate
* Clear distinction between normal and attack behavior
<img width="1698" height="751" alt="Screenshot 2026-04-27 100433" src="https://github.com/user-attachments/assets/60c4a004-035b-4a80-930a-a25e8d129117" />


### 🧠 Insight:

Dashboard visualization enables:

* Rapid identification of attack timelines
* Understanding of alert severity distribution
* Efficient incident triaging

---

## 🔗 Event Correlation Model

Multiple Failed Logins (Event ID 4625)
+
High Alert Frequency
+
Consistent Source Identifier
↓
Confirmed Brute Force Attack

### 🧠 Insight:

Effective threat detection in SOC environments relies on **correlating multiple weak signals** to form a strong, actionable alert.

---

## 🧬 MITRE ATT&CK Alignment

| Activity             | Technique         | ID    |
| -------------------- | ----------------- | ----- |
| Brute Force          | Credential Access | T1110 |
| PowerShell Execution | Command Execution | T1059 |
| Nmap Reconnaissance  | Network Discovery | T1046 |

---

## ⚠️ Detection Gaps & Limitations

### Identified Limitations:

* Ineffective detection of reconnaissance activity
* Minimal alerting for PowerShell execution

### Root Cause Analysis:

* Dependence on default SIEM rule sets
* Lack of advanced detection engineering
* Limited log enrichment and correlation

### 🎯 SOC Insight:

Detection gaps are a natural part of SOC operations and highlight the importance of:

* Continuous rule tuning
* Threat hunting practices
* Adaptive detection strategies

---

## 🎯 Overall SOC Assessment

* Brute-force attack was **successfully detected and analyzed**
* No evidence of system compromise observed
* Key detection gaps identified in:

  * Reconnaissance phase
  * Execution-level monitoring

---

## 🧠 Analyst Verdict

The system experienced a simulated brute-force attack characterized by high-frequency authentication failures and distinct anomaly patterns in log activity.

While detection of credential-based attacks was strong, limited visibility into reconnaissance and execution phases highlights the need for improved detection engineering and SIEM optimization.

---

## 🚀 Key Takeaways

* SIEM performance depends heavily on configuration and rule tuning
* Log correlation is essential for accurate threat detection
* Behavioral patterns help distinguish normal vs malicious activity
* Detection gaps must be continuously identified and addressed
* Effective SOC operations require both tools and analytical expertise

<img width="1609" height="423" alt="Screenshot 2026-04-29 121705" src="https://github.com/user-attachments/assets/705beca2-eaf3-4eb8-8419-f5567a61369c" />

