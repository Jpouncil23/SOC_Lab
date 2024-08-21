# SOC_Lab( Work in progress)

## Objective
The objective of this lab is to deepen my understanding of security concepts and the operations of a Security Operations Center (SOC). By designing and implementing my own lab environment, I aim to gain hands-on experience with logging and monitoring practices, and to become proficient in using the tools commonly employed in a SOC.



### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.
- Logging and monitoring 

### Tools Used
- Azure
- SSMS(sequal server managment studio)
- SQL server evaluation
- Azure Active Directory
- Azure Sentinal(SIEM)
- Microsoft Defender
- KQL
- Virtual Machines 
## Overview
In this lab, I have created two virtual machines: one running Windows and the other running Linux. I've set up a honeynet with live traffic, intentionally making the Windows virtual machine vulnerable by disabling its firewalls and creating a SQL database within it. This configuration is designed to lure attackers to target both the SQL database and the Windows machine itself. The Linux machine serves as an additional logging point, allowing me to capture data from potential attackers. All of this is hosted in the Azure cloud. Arrows in the diagram point to the Log Analytics Workspace, where logs from AAD/Tenant Logs, Management Plane Logs, and Data Plane Logs have been ingested. From there, I've configured Azure Sentinel, which references the Log Analytics Workspace, enabling me to create maps and incidents based on the collected data. 
![SOC_DIAGRAM drawio](https://github.com/user-attachments/assets/44a174e7-c372-48eb-adba-0d99c9c2be28)
BEFORE SECURING ENVIRONMENT FROM LAST 24 HOURS
![Screenshot 2024-08-20 204759](https://github.com/user-attachments/assets/c6aac3fa-1a13-463b-a526-621ea0b00ae7)
![Screenshot 2024-08-20 204936](https://github.com/user-attachments/assets/08b470da-a04d-4e64-9a12-af0ea1a4a7bc)
![Screenshot 2024-08-20 205224](https://github.com/user-attachments/assets/bd4edf7d-3ec2-481a-a965-139752c4c3b5)
![Screenshot 2024-08-20 205405](https://github.com/user-attachments/assets/d2c62c1e-5d82-447b-bde6-56353f5c4980)




I have configured 14 different rules in Microsoft Sentinel to trigger alerts and generate incidents.
![Screenshot 2024-08-20 192024](https://github.com/user-attachments/assets/bef43d1a-c208-448a-b2c9-2b75799b6701)
Inspecting one of the incidents reported I found a successful brute force attack on my windows VM from Iran
![Screenshot 2024-08-20 194630](https://github.com/user-attachments/assets/49c79b02-8b73-4eba-b3aa-be5322467e57)
![Screenshot 2024-08-20 194955](https://github.com/user-attachments/assets/fdaf4400-03cd-4923-901f-4733b1184e08)

















