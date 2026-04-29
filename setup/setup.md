# ⚙️ SOC Lab Setup Guide – Wazuh SIEM

## 📌 Overview

This document outlines the setup of a **Security Operations Center (SOC) simulation lab** using Wazuh SIEM.
The lab is designed to replicate a real-world Blue Team environment focused on **log collection, threat detection, and security monitoring**.

### 🔍 Key Objective

To build a functional SOC pipeline capable of:

* Collecting endpoint logs
* Detecting suspicious activities
* Monitoring security events in real time

---

## 🏗️ Lab Architecture

```
Kali Linux (Attacker)
        ↓
Windows 11 (Wazuh Agent + Sysmon)
        ↓
Wazuh Manager (Amazon Linux 2023)
        ↓
Wazuh Dashboard (SIEM)
```

---

## 🖥️ Environment Setup

| Machine      | Role            | OS                |
| ------------ | --------------- | ----------------- |
| Wazuh Server | SIEM            | Amazon Linux 2023 |
| Windows 11   | Target Endpoint | Windows 11        |
| Kali Linux   | Attacker        | Kali Linux        |

---

## 🌐 Network Configuration

* All machines connected via **NAT Network**
* Ensure connectivity using:

```
ping <target-ip>
```

---

## ⚙️ Step 1: Wazuh Server Setup

### 1. Import Wazuh OVA

* Import into VMware / VirtualBox
* Start the virtual machine

### 2. Access Dashboard

```
https://<WAZUH_SERVER_IP>
```

### 3. Verify Services

Ensure the following services are running:

* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard

---

## 🖥️ Step 2: Windows Agent Setup

### 1. Install Wazuh Agent

* Download from Wazuh Dashboard
* Install on Windows 11 machine

### 2. Configure Agent

Edit configuration file:

```
C:\Program Files (x86)\ossec-agent\ossec.conf
```

Update server IP:

```
<address><WAZUH_SERVER_IP></address>
```

### 3. 🔐 Agent Authentication (Critical Step)

```
agent-auth.exe -m <WAZUH_SERVER_IP>
```

### 4. Start Agent

```
net start wazuh-agent
```

---

## 🔍 Step 3: Sysmon Configuration

### 1. Install Sysmon

Download from official Microsoft source

### 2. Apply Configuration

Use community config:

* SwiftOnSecurity Sysmon Config

### 3. Install

```
Sysmon64.exe -i sysmonconfig.xml
```

### 📊 Purpose

Sysmon enhances visibility by providing:

* Process creation logs
* Network activity
* File & registry monitoring

---

## 🐉 Step 4: Kali Linux Setup

* Ensure Kali is connected to same network
* Verify connectivity with Windows machine

### 🛠️ Tools Used

* Hydra (Brute Force)
* Nmap (Port Scanning)

---

## 🧠 Step 5: Detection-Oriented Setup

A SOC lab is incomplete without detection capabilities.

### 🎯 Detection Goals

* Detect brute-force login attempts
* Identify suspicious PowerShell activity
* Monitor abnormal process execution
* Track system-level changes

---

## 🔍 Log & Detection Verification

### Key Event IDs

* **4625** → Failed login attempts
* **Sysmon Event ID 1** → Process creation

### Validation Checks

* Logs visible in Wazuh Dashboard
* Alerts generated for simulated attacks
* Correlation between logs and attack activity

---

## ⚠️ Common Issues & Fixes

### ❌ Agent Not Connecting

* Run `agent-auth.exe`
* Verify correct server IP

### ❌ No Logs in Dashboard

* Check Sysmon installation
* Restart Wazuh agent

### ❌ No Detection Alerts

* Default rules may not detect all attacks
* Requires rule tuning

---

## ✅ Final Validation Checklist

* [ ] Wazuh dashboard accessible
* [ ] Agent connected and authenticated
* [ ] Sysmon logs visible
* [ ] Kali machine reachable
* [ ] Alerts generated in dashboard

---

## 🎯 Outcome

After successful setup:

* Log collection pipeline is established
* Endpoint visibility is achieved
* Real-time detection is operational

---

## 🧠 Key Insight

> Detection in a SOC environment is not automatic — it requires continuous tuning, log analysis, and understanding of attack patterns.

---
