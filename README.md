# velociraptor-edr-lab



\# Velociraptor Detection Lab



This repository contains a hands-on cybersecurity lab using \[Velociraptor](https://www.velociraptor.app/), an open-source Endpoint Detection and Response (EDR) tool designed for threat hunting and digital forensics. The lab simulates common endpoint attack techniques on Windows systems and demonstrates how to detect and investigate them using Velociraptor's powerful querying and forensic capabilities.



---



\## Lab Architecture



\- \*\*Velociraptor Server:\*\* Ubuntu VM  

\- \*\*Velociraptor Agent:\*\* Windows 10 VM  

\- \*\*Network:\*\* Host-only or NAT setup for communication between server and agent



---



\## Repository Contents



\- `velociraptor-server.md` - Installation and setup instructions for the Velociraptor server  

\- `velociraptor-agent.md` - Steps to install and configure the Velociraptor agent on Windows  

\- `simulations/` - Contains markdown files documenting attack simulations and detection techniques, including:  

&nbsp; - Credential dumping  

&nbsp; - Persistence via registry autorun keys  

&nbsp; - Remote Access Trojan (RAT) simulations  



---



\## Attack Simulations Overview



| #   | Attack Type         | Description                             |

|------|--------------------|-----------------------------------------|

| 1    | Credential Access  | Simulate Mimikatz and detect LSASS memory access  |

| 2    | Persistence        | Create suspicious autorun registry keys and hunt for them |

| 3    | Command \& Control  | Simulate PowerShell reverse shells or RAT activity   |



---



\## Prerequisites



\- Basic knowledge of command line and PowerShell  

\- Running virtual machines for Ubuntu (Velociraptor Server) and Windows 10 (Agent)  

\- Installed Git and Velociraptor binaries  



---



\## Getting Started



1\. Follow `velociraptor-server.md` to set up the Velociraptor server.  

2\. Follow `velociraptor-agent.md` to install and configure the Windows agent.  

3\. Perform attack simulations described in `simulations/` folder.  

4\. Use Velociraptor hunts and queries to detect and analyze the simulated attacks.



---



\## Resources



\- \[Velociraptor Official Documentation](https://docs.velociraptor.app/)  

\- \[Velociraptor GitHub Repository](https://github.com/Velocidex/velociraptor)  



---



\## Author



Loksharan Saravanan  

Email: loksharan.soc@gmail.com  

GitHub: \[github.com/loksharan-soc](https://github.com/loksharan-soc)  

LinkedIn: \[linkedin.com/in/loksharan](https://linkedin.com/in/loksharan)



---



\## License



This project is for educational purposes only.





