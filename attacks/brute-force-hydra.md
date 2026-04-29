# 🔐 Brute Force Attack Detection & Analysis using Hydra

## 📌 Objective

To simulate a real-world credential brute-force attack and analyze how Wazuh SIEM detects repeated authentication failures.

---

## ⚙️ Attack Environment

| Component        | Details                           |
| ---------------- | --------------------------------- |
| Attacker Machine | Kali Linux                        |
| Target System    | Windows 11 (Wazuh Agent + Sysmon) |
| Tool             | Hydra                             |
| Protocol         | SSH / RDP                         |
| SIEM             | Wazuh                             |

---

## 🚀 Attack Execution

### Command Used

hydra -l administrator -P passwords.txt <target-ip> ssh

---

## 🧪 Attack Behavior

* Multiple login attempts executed rapidly
* High-frequency authentication requests
* Same source IP used continuously

This behavior clearly indicates automated brute-force activity.

---

## 🔍 Log Analysis & Detection

### 📸 Wazuh Detection

<img width="853" height="532" alt="Screenshot 2026-04-27 100502" src="https://github.com/user-attachments/assets/e15e1b81-22dc-4d2f-b1a9-5d734ef4d06e" />


*Figure 2: Wazuh dashboard showing multiple failed login alerts*

### Key Indicators

* **Event ID:** 4625 (Failed Login)
* Repeated authentication failures
* High volume of logs in short duration

---

## 📊 Detection Summary

| Metric           | Observation             |
| ---------------- | ----------------------- |
| Detection Status | ✔ Successfully Detected |
| Alert Volume     | High                    |
| Visibility       | Clear                   |

---

## 🧠 Analysis

Wazuh SIEM successfully detected the brute-force attack by identifying:

* Repeated failed login attempts
* High-frequency request patterns
* Consistent attacker source

These indicators strongly confirm automated credential attack behavior.

---

## 🎯 SOC Perspective

From a SOC analyst viewpoint:

* Attack was clearly identifiable
* Alerts were generated in real-time
* Investigation was straightforward

This demonstrates effective alert monitoring and incident detection capability.

---

## 🧾 Conclusion

The brute-force attack was successfully simulated and detected using Wazuh SIEM.

The combination of authentication logs, alert spikes, and repeated behavior enabled accurate detection of the attack, showcasing the effectiveness of SIEM in real-time threat monitoring.

---
