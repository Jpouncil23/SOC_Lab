# SOC_Lab

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
- SIEM
- SSMS(sequal server managment studio)
- SQL server evaluation
- Azure Active Directory
- Azure Sentinal(SIEM)
-  
## Steps
Using Microsoft Azure I created 2 virtual machines setting network rules to open all internet traffic to create a honey net and bring in live traffic for the SOC lab

![Screenshot 2024-06-27 160120](https://github.com/Jpouncil23/SOC_Lab/assets/163768012/26ceb360-d3f0-4804-a925-a1ffde5ce6aa)
![Screenshot 2024-06-27 160556](https://github.com/Jpouncil23/SOC_Lab/assets/163768012/01e8d706-62c1-494f-9dc8-d0e967a8813b)
*note after connecting to the windows VM via RDP I disabled the windows firewalls and setup a SQL database. By doing so this sets up a honeynet and entices attackers that will help produce more logs for my SOC lab that I can anaylze.




