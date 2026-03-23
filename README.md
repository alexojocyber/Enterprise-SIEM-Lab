# 🚨 Enterprise SIEM Lab: Brute Force Detection & Investigation (SOC Simulation)

---

# 🎯 Project Overview

This project simulates a real-world Security Operations Center (SOC) investigation using Linux authentication logs to detect and respond to a brute-force attack.

The objective of this lab is to demonstrate hands-on cybersecurity skills including:

- Threat detection
- Log analysis
- Incident investigation
- Security monitoring
- System hardening using PAM

This project follows a structured SOC workflow from detection to response and mitigation.

---

# 🧪 Scenario

An attacker attempts to gain unauthorized access to a Linux system by performing multiple failed login attempts against a user account.

This activity simulates a **brute-force attack**, where repeated password attempts are used to guess valid credentials.

During this investigation, suspicious login behavior was simulated and analyzed to:

- Detect authentication failures
- Investigate login attempts
- Identify Indicators of Compromise (IOCs)
- Implement account lockout protection
- Validate mitigation effectiveness

---

# 🏗️ Lab Architecture

## Environment Setup

- System: Ubuntu Linux
- Log Source: `/var/log/auth.log`
- Authentication Method: PAM (Pluggable Authentication Modules)
- Test User Created: `testuser`

Authentication logs were monitored to detect failed login attempts and simulate attacker behavior.

---

# 🛠️ Technologies Used

- Ubuntu Linux
- Linux Authentication Logs
- PAM (Pluggable Authentication Modules)
- Nano Text Editor
- Bash Commands
- MITRE ATT&CK Framework

---

# 🎯 Learning Objectives

This lab was designed to build practical SOC analyst skills, including:

- Monitoring authentication logs
- Detecting brute-force login attempts
- Identifying suspicious login behavior
- Investigating authentication failures
- Implementing account lockout controls
- Validating security configurations
- Documenting incident response steps

---

# 🚨 Detection Logic

Suspicious activity was defined as:

- More than **3 failed login attempts**
- Within a short period of time
- Targeting the **same user account**

This pattern is commonly associated with **brute-force login attacks**.

---

# 🔍 Investigation Timeline

## Step 1 — Monitor Authentication Logs

Authentication logs were monitored in real-time using:
```bash
sudo tail -f /var/log/auth.log
```

## Step 2 — Identify Failed Login Attempts

Failed login attempts were extracted using:
```bash
sudo cat /var/log/auth.log | grep "authentication failure"
```

A total of **12 failed login attempts** were recorded during the attack simulation.

## Step 3 — Identify Targeted User

The affected user account was identified using:
```bash
sudo cat /var/log/auth.log | grep testuser
```

Repeated authentication failures confirmed that the `testuser` account was being targeted.

---

# 🚨 Indicators of Compromise (IOCs)

The following suspicious indicators were identified:

- **Targeted User:** testuser
- **Failed Login Attempts:** 12
- **Log Source:** /var/log/auth.log
- **Activity:** Multiple authentication failures
- **Attack Type:** Brute Force Attempt

These indicators confirmed repeated unauthorized login attempts.

---

## ⚠️ Incident Recovery — PAM Authentication Failure

During the implementation of account lockout protection using PAM faillock, 
an incorrect configuration caused authentication failure, preventing login access.

### Root Cause

Misconfigured PAM faillock rules disrupted the authentication stack, 
causing the system to reject login attempts before password validation.

### Resolution Steps

1. Booted into recovery mode
2. Restored default PAM configuration:

pam-auth-update

3. Reinstalled PAM modules:

apt-get install --reinstall libpam-modules libpam-runtime

4. Reset faillock records:

faillock --reset

5. Rebooted system successfully

System login functionality was restored.

# 🎯 MITRE ATT&CK Mapping

| Tactic | Technique | Description |
|--------|-----------|-------------|
| Credential Access | T1110 — Brute Force | Repeated password attempts used to gain unauthorized access |

---

# 🔒 Response & Mitigation

To prevent brute-force attacks, account lockout protection was implemented using PAM faillock.

## Configuration Applied

The following settings were configured in `/etc/security/faillock.conf`:
```
deny = 3
fail_interval = 900
unlock_time = 600
```

## Configuration Explanation

- **deny = 3** — Locks the account after 3 failed login attempts.
- **fail_interval = 900** — Counts failed attempts within 15 minutes.
- **unlock_time = 600** — Unlocks the account after 10 minutes.

These controls help protect systems from repeated login attacks.

---

# ✅ Validation Testing

Multiple failed login attempts were simulated using:
```bash
su testuser
```

After exceeding the allowed number of failed attempts, further login attempts returned:
```
Permission denied
```

---

# 📸 Evidence

## Failed Login Attempt

<img width="556" height="644" alt="attack-attempt" src="https://github.com/user-attachments/assets/1361e195-8230-4df2-a3c1-51d677b91392" />

## Authentication Log Output

<img width="1852" height="962" alt="failed-login-logs" src="https://github.com/user-attachments/assets/5a756be0-46d0-4aff-973c-fd2e39aa9f9f" />

## Failed Login Detection

<img width="1852" height="844" alt="authentication-failure-timeline" src="https://github.com/user-attachments/assets/fcb552a1-faee-44e0-be27-e6d9040b1fd8" />

## Account Lockout Confirmation

<img width="1858" height="602" alt="account-lockout-working" src="https://github.com/user-attachments/assets/684eb406-77ba-491d-9759-ab56286f8b06" />

---

# 🧠 Lessons Learned

This lab provided valuable cybersecurity insights:

- Repeated authentication failures often indicate brute-force attacks.
- Monitoring authentication logs helps detect suspicious behavior early.
- PAM account lockout policies significantly reduce attack risk.
- Proper configuration strengthens Linux authentication security.
- Structured documentation improves incident investigation clarity.

---

# 📋 Project Status

- ✅ Created test user account
- ✅ Simulated brute-force login attempts
- ✅ Monitored authentication logs
- ✅ Identified failed login attempts
- ✅ Detected targeted user account
- ✅ Implemented account lockout protection
- ✅ Validated mitigation effectiveness
- ✅ Documented investigation findings

---

# 🚀 Future Improvements

Planned enhancements include:

- Integrating Wazuh SIEM
- Creating custom detection rules
- Implementing alert notifications
- Expanding attack simulation scenarios
- Automating log monitoring

---

# 👨‍💻 Author

**Alex Ojo**
Cybersecurity Student | SOC Analyst Trainee

🔗 [LinkedIn](https://linkedin.com/in/alex-o-ojo-ab9252185)
🔗 [GitHub](https://github.com/alexojocyber)
