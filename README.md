# 🚨 Enterprise SIEM Lab: Brute Force Detection & Investigation (SOC Simulation)

## 🎯 Project Overview
This project focuses on building a production-style Security Information and Event Management (SIEM) lab using Wazuh to simulate real-world SOC operations.

The goal is to demonstrate practical cybersecurity skills including:
- Threat detection  
- Log analysis  
- Incident investigation  
- Security monitoring  

---

## 🧪 Scenario
An attacker attempts to gain unauthorized access to a Linux system by performing multiple failed login attempts (brute force attack).

This lab simulates how a SOC analyst would:
- Detect suspicious login activity  
- Investigate authentication logs  
- Identify Indicators of Compromise (IOCs)  
- Respond and implement mitigation controls  

---

## 🏗️ Architecture
**Lab Environment:**
- Wazuh Manager (Ubuntu Server 22.04)
- Windows 10 Agent
- Ubuntu Desktop Agent
- Log sources: authentication logs, system logs
- Custom detection rules mapped to MITRE ATT&CK

---

## 📋 Project Roadmap
- [ ] Week 1: Infrastructure deployment  
- [ ] Week 2: Detection engineering  
- [ ] Week 3: Incident investigation (Brute Force Attack)  
- [ ] Week 4: Documentation & reporting  

---

## 🛠️ Technologies
- Wazuh SIEM  
- Ubuntu Server 22.04  
- Windows 11 Pro  
- VMware Workstation  
- MITRE ATT&CK Framework  

---

## 🎯 Learning Objectives
- Understand how SIEM tools collect and analyze logs  
- Detect brute force attack patterns in authentication logs  
- Perform structured incident investigations  
- Map findings to MITRE ATT&CK framework  
- Apply system hardening techniques to prevent attacks  

---

## 📝 Documentation
🚧 Work in progress — detailed investigation reports and findings will be added as the lab progresses.

---
## 🚨 Detection Logic

Suspicious activity is detected when:

- More than 3 failed login attempts
- Within a short period of time
- Targeting the same user account
This pattern indicates a possible brute force attack.

## 📸 Evidence

### Failed Login Attempt

<img width="556" height="644" alt="attack-attempt (Copy)" src="https://github.com/user-attachments/assets/1361e195-8230-4df2-a3c1-51d677b91392" />


### Authentication Log Output

<img width="1852" height="962" alt="failed-login-logs" src="https://github.com/user-attachments/assets/5a756be0-46d0-4aff-973c-fd2e39aa9f9f" />



## 👤 Author
**Alex Ojo**  
🔗 LinkedIn: https://linkedin.com/in/alex-o-ojo-ab9252185  
💻 GitHub: https://github.com/alexojocyber
