# Wazuh SOC Home Lab

A hands on Security Operations Center (SOC) home lab built to practice **security monitoring, endpoint telemetry analysis, detection engineering, file integrity monitoring, incident response, and security investigation** using Wazuh.

---

## 🎯 Project Objective

The objective of this project was to build and operate a small SOC environment where I could generate security activity, collect endpoint telemetry, analyze events, create detections, configure automated response, and investigate security incidents.

The project followed a practical workflow:

```text
Build → Generate Activity → Collect Telemetry → Analyze
→ Detect → Respond → Investigate → Document
```

---

## 🏗️ Lab Environment

The lab consists of:

- **Wazuh Server / Manager** — Centralized security monitoring and analysis
- **Ubuntu Server** — Monitored Linux endpoint
- **Windows 10** — Monitored Windows endpoint
- **Sysmon** — Windows & Linux endpoint telemetry
- **Wazuh Dashboard** — Security event monitoring and visualization
- **Active Response** — Automated response to detected SSH activity

---

## 🔧 What I Built

### 1. Wazuh Server Deployment

Deployed and configured the Wazuh server environment and prepared the platform for endpoint monitoring.

### 2. Agent Deployment & Endpoint Telemetry

Connected both Ubuntu Server and Windows 10 endpoints to Wazuh.

Configured Sysmon on the Windows environment to provide additional endpoint telemetry.

### 3. Telemetry Generation & Analysis

Generated controlled security activity and practiced reading and interpreting endpoint telemetry.

Examples included:

- User logon activity
- File creation
- File deletion
- Guest account enable/disable activity
- Other endpoint security events

The goal was to understand **what normal and suspicious activity looks like in endpoint telemetry**.

### 4. Wazuh Dashboard

Built and configured the Wazuh Dashboard to monitor security events and visualize collected telemetry.

The dashboard was used to:

- Monitor alerts
- Review endpoint activity
- Investigate security events
- Analyze detection results

### 5. File Integrity Monitoring & Detection

Configured File Integrity Monitoring (FIM) and created detection logic for file activity.

This provided hands on experience with detecting changes to monitored files and analyzing the resulting security events.

### 6. Active Response

Configured Wazuh Active Response for SSH authentication activity.

When repeated SSH authentication failures were detected, Wazuh automatically executed the `firewall-drop` response to block the source IP.

### 7. Security Investigation

Conducted an investigation of an SSH authentication incident generated within the lab.

The investigation covered:

- Multiple failed SSH authentication attempts
- Source and destination identification
- Wazuh alert analysis
- Rule identification
- Active Response
- Source IP blocking
- Impact assessment
- Security recommendations

[View the full investigation report](./investigation/SSH-Investigation-Report.md)

---

## 🚨 Detection & Response Example

### SSH Authentication Abuse

A controlled SSH authentication scenario was generated against the monitored Ubuntu server.

Three failed authentication attempts were observed from the same source IP.

Wazuh generated the following detection:

```text
Multiple SSH login failures observed from the same source IP
Rule ID: 100101
```

The configured Active Response then executed:

```text
firewall-drop
```

The source IP was blocked automatically.

```text
SSH Authentication Attempts
            ↓
     Failed Attempts
            ↓
     Wazuh Detection
            ↓
       Rule 100101
            ↓
    Active Response
            ↓
      firewall-drop
            ↓
       IP Blocked
            ↓
      Investigation
```

---

## 📸 Lab & Investigation

Screenshots below demonstrate the environment, monitoring, detection, and response capabilities developed during the project.

### Wazuh Dashboard

<img width="1917" height="1137" alt="image" src="https://github.com/user-attachments/assets/f1101dd0-f8c1-4f5e-aedf-963d426bb7d1" />

### File Integrity Monitoring

<img width="1917" height="1137" alt="setting-basic-monitoring" src="https://github.com/user-attachments/assets/ae29faf1-08e4-4d2f-988f-69dd896b1632" />

### SSH Detection and Active Response

<img width="1490" height="696" alt="Screenshot 2026-10-03 190224" src="https://github.com/user-attachments/assets/5ae02229-19c1-4948-bb54-01cc11650e67" />

## 🧠 Skills Demonstrated

- Security Operations Center (SOC) workflows
- SIEM monitoring with Wazuh
- Linux security monitoring
- Windows endpoint monitoring
- Sysmon
- Security telemetry analysis
- Log analysis
- Detection engineering
- File Integrity Monitoring
- SSH security monitoring
- Wazuh Active Response
- Automated IP blocking
- Incident investigation
- Incident documentation

---

## 📚 Project Report

**Security Investigation Report**

[View the SSH investigation report](./investigation/SSH-Investigation-Report.md)

---

