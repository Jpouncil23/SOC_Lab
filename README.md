# SOC Analyst Lab — Azure Honeynet

[![Cloud](https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue)](https://github.com)
[![SIEM](https://img.shields.io/badge/SIEM-Azure%20Sentinel-orange)](https://github.com)
[![Status](https://img.shields.io/badge/Status-Complete-success)](https://github.com)

## Objective

The objective of this lab is to gain hands-on experience as a SOC Analyst by building a cloud-based environment in Azure. I deployed a vulnerable VM as a honeynet, set up logging and monitoring with Log Analytics and Azure Sentinel, and then applied NIST security controls to harden the environment. The goal was to compare security metrics before and after hardening to see how effective those controls actually are.

## Tools Used

| Tool | Purpose |
|------|---------|
| **Microsoft Azure** | Cloud platform hosting the entire lab |
| **Azure Sentinel** | SIEM — threat detection, alert rules, and incident management |
| **Log Analytics Workspace** | Central hub for ingesting and querying logs |
| **Microsoft Defender for Cloud** | Cloud security monitoring and alerts |
| **Azure Active Directory** | Identity and access management |
| **SSMS (SQL Server Management Studio)** | Managing the SQL database on the Windows VM |
| **SQL Server Evaluation** | Database running on the honeynet to attract attackers |
| **KQL (Kusto Query Language)** | Writing queries to analyze log data |
| **NIST 800-53** | Security controls framework used to harden the environment |
| **Incident Response Playbook** | Structured response process for handling incidents |

## Skills Learned

- Setting up and managing cloud environments in Azure
- Deploying and running a honeynet with live traffic
- Windows and Linux server administration
- Log management and analysis (AAD, Management Plane, Data Plane)
- Using Azure Sentinel for threat detection and incident management
- Writing KQL queries to investigate security events
- Implementing NIST 800-53 security controls and hardening an environment
- Comparing security metrics to measure the impact of hardening

## Overview

In this lab, I created two virtual machines — one running Windows and the other running Linux. I set up a honeynet with live traffic, intentionally making the Windows VM vulnerable by disabling its firewalls and creating a SQL database inside it. The idea was to attract attackers to target both the SQL database and the Windows machine itself. The Linux machine serves as an additional logging point so I could capture data from potential attackers.

All of this is hosted in Azure. The arrows in the diagram below point to the Log Analytics Workspace, where logs from AAD/Tenant Logs, Management Plane Logs, and Data Plane Logs are all being ingested. From there, I configured Azure Sentinel to reference the Log Analytics Workspace, which let me create attack maps and incidents based on the collected data.

To wrap up the lab, I compared metrics from the unsecured environment over 24 hours against a secured environment 24 hours after implementing NIST 800-53 security controls.

![SOC Lab Architecture Diagram](https://github.com/user-attachments/assets/44a174e7-c372-48eb-adba-0d99c9c2be28)

---

## Before Securing the Environment

These are the metrics I captured over a 24-hour period with the environment completely open and unsecured.

| Metric | Count |
|--------|-------|
| **Start Time** | 8/19/2024 20:24:06 |
| **Stop Time** | 8/20/2024 20:24:06 |
| **Security Events (Windows VMs)** | 19,284 |
| **Syslog (Linux VMs)** | 7,862 |
| **SecurityAlert (Microsoft Defender for Cloud)** | 8 |
| **SecurityIncident (Sentinel Incidents)** | 234 |
| **NSG Inbound Malicious Flows Allowed** | 268 |

### Attack Maps (Before Hardening)

These maps show where the attacks were coming from while the environment was left open.

![Windows RDP Auth Failures](https://github.com/user-attachments/assets/c6aac3fa-1a13-463b-a526-621ea0b00ae7)

![Linux SSH Auth Failures](https://github.com/user-attachments/assets/08b470da-a04d-4e64-9a12-af0ea1a4a7bc)

![MS SQL Auth Failures](https://github.com/user-attachments/assets/bd4edf7d-3ec2-481a-a965-139752c4c3b5)

![NSG Malicious Allowed In](https://github.com/user-attachments/assets/d2c62c1e-5d82-447b-bde6-56353f5c4980)

---

## Sentinel Alert Rules and Incidents

I configured 14 different rules in Microsoft Sentinel to trigger alerts and generate incidents.

![Sentinel Analytics Rules](https://github.com/user-attachments/assets/bef43d1a-c208-448a-b2c9-2b75799b6701)

One of the incidents I found was a successful brute force attack on my Windows VM originating from Iran.

![Brute Force Incident](https://github.com/user-attachments/assets/49c79b02-8b73-4eba-b3aa-be5322467e57)

![Incident Investigation](https://github.com/user-attachments/assets/9a60e5e3-c57d-4c28-8e31-f9afa22aa6b4)

---

## After Securing the Environment

After applying NIST 800-53 security controls and hardening the system, I captured metrics for another 24 hours. All map queries came back with no results — there were zero instances of malicious activity detected after hardening.

| Metric | Count |
|--------|-------|
| **Start Time** | 8/24/2024 21:27:55 |
| **Stop Time** | 8/25/2024 21:27:55 |
| **Security Events (Windows VMs)** | 9,538 |
| **Syslog (Linux VMs)** | 1 |
| **SecurityAlert (Microsoft Defender for Cloud)** | 0 |
| **SecurityIncident (Sentinel Incidents)** | 0 |
| **NSG Inbound Malicious Flows Allowed** | 0 |

---

## Results — Before vs. After Hardening

| Metric | Change After Securing |
|--------|----------------------|
| **Security Events (Windows VMs)** | -50.54% |
| **Syslog (Linux VMs)** | -99.99% |
| **SecurityAlert (Microsoft Defender for Cloud)** | -100% |
| **SecurityIncident (Sentinel Incidents)** | -100% |
| **NSG Inbound Malicious Flows Allowed** | -100% |

The results speak for themselves. After applying security controls, malicious traffic dropped to zero across the board — no alerts, no incidents, and no malicious flows allowed through the NSGs. Windows security events were cut in half, and Linux syslog entries dropped from nearly 8,000 down to 1.

---

## Author

**Justin**
IT Professional

---

*Last Updated: August 2024*
