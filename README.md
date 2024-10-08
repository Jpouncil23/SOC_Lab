# SOC_Lab

## Objective
The objective of this lab is to gain hands-on experience as a SOC Analyst by designing and implementing a secure cloud-based environment within Azure. This includes deploying a vulnerable virtual machine as a honeynet, configuring a comprehensive logging and monitoring system using Log Analytics and Azure Sentinel, and applying NIST security controls. The lab also aims to assess the effectiveness of these measures through comparative analysis of security metrics from both unsecured and secured environments.

### Skills Learned

- Proficiency in virtualization and cloud management (Azure).
- Skilled in deploying and managing a honeynet.
- Advanced Windows and Linux server administration.
- Expertise in log management and analysis (AAD, Management Plane, Data Plane).
- Practical experience with Azure Sentinel for threat detection and incident management.
- Implementation of NIST security controls and environment hardening.
  
### Tools Used
- Azure
- SSMS(sequal server managment studio)
- SQL server evaluation
- Azure Active Directory
- Azure Sentinal(SIEM)
- Microsoft Defender
- KQL (Kusto Query Language)
- Virtual Machines
- NIST
- Incident Responce Playbook
## Overview
In this lab, I have created two virtual machines: one running Windows and the other running Linux. I've set up a honeynet with live traffic, intentionally making the Windows virtual machine vulnerable by disabling its firewalls and creating a SQL database within it. This setup is designed to attract attackers to target both the SQL database and the Windows machine itself. The Linux machine serves as an additional logging point, allowing me to capture data from potential attackers. All of this is hosted in the Azure cloud. Arrows in the diagram point to the Log Analytics Workspace, where logs from AAD/Tenant Logs, Management Plane Logs, and Data Plane Logs have been ingested. From there, I've configured Azure Sentinel to reference the Log Analytics Workspace, enabling the creation of maps and incidents based on the collected data. To complete the lab environment, I will present metrics comparing an unsecured environment over the last 24 hours with a secure environment 24 hours after implementing NIST 800-53 security controls and hardening the system.

![SOC_DIAGRAM drawio](https://github.com/user-attachments/assets/44a174e7-c372-48eb-adba-0d99c9c2be28)

METRICS BEFORE SECURING ENVIRONMENT 
| Metrics                                         |         |
|-----------------------------------------------|----------------------------|
| Start Time  | 8/19/2024 20:24:06|
| Stop Time  | 8/20/2024 20:24:06|
| Security Events (Windows VMs)    | 19284|
| Syslog (Linux VMs)   | 7862|
| SecurityAlert (Microsoft Defender for Cloud)    |8|
| SecurityIncident (Sentinel Incidents)|234|
| NSG Inbound Malicious Flows Allowed  | 268|

![Screenshot 2024-08-20 204759](https://github.com/user-attachments/assets/c6aac3fa-1a13-463b-a526-621ea0b00ae7)
![Screenshot 2024-08-20 204936](https://github.com/user-attachments/assets/08b470da-a04d-4e64-9a12-af0ea1a4a7bc)
![Screenshot 2024-08-20 205224](https://github.com/user-attachments/assets/bd4edf7d-3ec2-481a-a965-139752c4c3b5)
![Screenshot 2024-08-20 205405](https://github.com/user-attachments/assets/d2c62c1e-5d82-447b-bde6-56353f5c4980)

I configured 14 different rules in Microsoft Sentinel to trigger alerts and generate incidents.
![Screenshot 2024-08-20 192024](https://github.com/user-attachments/assets/bef43d1a-c208-448a-b2c9-2b75799b6701)
One of the incidents reported I found a successful brute force attack on my windows VM from Iran
![Screenshot 2024-08-20 194630](https://github.com/user-attachments/assets/49c79b02-8b73-4eba-b3aa-be5322467e57)
![Screenshot 2024-08-21 190246](https://github.com/user-attachments/assets/9a60e5e3-c57d-4c28-8e31-f9afa22aa6b4)

METRICS AFTER SECURING ENVIRONMENT

All map queries yielded no results, as there were no instances of malicious activity detected during the 24 hours following the hardening process
| Metrics                                         |         |
|-----------------------------------------------|----------------------------|
| Start Time  |8/24/2024 21:27:55|
| Stop Time  | 8/25/2024 21:27:55|
| Security Events (Windows VMs)    | 9538|
| Syslog (Linux VMs)   | 1|
| SecurityAlert (Microsoft Defender for Cloud)    |0|
| SecurityIncident (Sentinel Incidents)|0|
| NSG Inbound Malicious Flows Allowed  | 0|

| RESULTS                                         |  Change after securing environment       |
|-----------------------------------------------|----------------------------|
| Security Events (Windows VMs)    | -50.54%|
| Syslog (Linux VMs)   | -99.99%|
| SecurityAlert (Microsoft Defender for Cloud)    |-100%|
| SecurityIncident (Sentinel Incidents)|-100%|
| NSG Inbound Malicious Flows Allowed  | -100%|













