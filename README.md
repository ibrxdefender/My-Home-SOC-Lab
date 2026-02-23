# My-Home-SOC-Lab
My Home SOC Lab Project

Overview

A hands‑on Security Operations Center home lab built using Splunk, Windows 10, Kali Linux, Sysmon, and real attack simulations.
 Table of Contents
• 	Overview
• 	Architecture
• 	Objectives
• 	Tools & Technologies
• 	Lab Topology
• 	Deployment Steps
• 	1. VirtualBox Environment Setup
• 	2. Splunk Enterprise Installation
• 	3. Universal Forwarder Setup
• 	4. Sysmon Deployment
• 	5. Data Onboarding in Splunk
• 	6. Kali Linux Attack Simulation
• 	7. Detection Engineering (SPL)
• 	8. Incident Investigation
• 	Splunk Searches
• 	Screenshots
• 	Results & Findings
• 	Future Improvements

Architecture
• 	VirtualBox hypervisor
• 	Windows 10 VM (monitored endpoint)
• 	Kali Linux VM (attacker machine)
• 	Splunk Enterprise Server
• 	Splunk Universal Forwarder
• 	Sysmon for detailed endpoint telemetry

🛠️ Tools & Technologies
Virtualisation = VirtualBox
SIEM = Splunk
Endpoint = Windows 10
Attacker = Kali linux
Logging = Sysmon, Windows Event Logs
Forwarding = Splunk Universal Forwarder
Simulation = Nmap, Hydra, Metasploit, Powershell abuse, reverse shells
Analysis = SPL, Dashboards, Alerts

Lab Topology
+-------------------+         +---------------------------+
| Windows 10 VM     | ----->  | Splunk Universal Forwarder |
| Sysmon + EventLog |         | (Log Forwarding)           |
+-------------------+         +---------------------------+
                                       |
                                       v
                            +----------------------+
                            | Splunk Enterprise   |
                            | (Indexing + Search) |
                            +----------------------+
                                       ^
                                       |
+-------------------+                  |
| Kali Linux VM     | ----------------+
| Attack Simulation |
+-------------------+

Deployment Steps

1. VirtualBox Environment Setup
• 	Installed VirtualBox
• 	Created Windows 10 VM
• 	Created Kali Linux VM
• 	Configured host‑only networking for isolated traffic


2. Splunk Enterprise Installation
• 	Installed Splunk Enterprise on Windows or Linux host
• 	Configured admin credentials
• 	Enabled receiving on port 9997
• 	Verified Splunk Web access


3. Universal Forwarder Setup
• 	Installed Splunk Universal Forwarder on Windows 10
• 	Configured forwarding to Splunk server
• 	Verified connection using splunk list forward-server


4. Sysmon Deployment
• 	Installed Sysmon using SwiftOnSecurity config
• 	Enabled detailed process, network, and registry logging
• 	Verified Sysmon events in Event Viewer

5. Data Onboarding in Splunk
Onboarded:
• 	Sysmon logs
• 	Security logs
• 	PowerShell logs
• 	Application logs
Verified logs in:
• 	index=wineventlog
• 	index-sysmon


6. Kali Linux Attack Simulation
Simulated attacks included:
• 	Nmap scanning
• 	Brute force attempts (Hydra)
• 	Reverse shell execution
• 	PowerShell exploitation
• 	Privilege escalation attempts

7. Detection Engineering (SPL)
Created SPL alerts for:
• 	Suspicious PowerShell commands
• 	Sysmon Event ID 1 anomalies
• 	Multiple failed logons
• 	Reverse shell behavior
• 	Network scanning patterns

8. Incident Investigation
Documented:
• 	Alerts triggered
• 	Timeline of events
• 	Affected user and host
• 	Root cause analysis
• 	Response actions taken

Splunk Searches

index=sysmon EventCode=1
| search Image="*powershell.exe"
| stats count by CommandLine, ParentImage, Computer

Network scanning detection:
index=sysmon EventCode=3
| stats count by DestinationIp, DestinationPort
| where count > 50

Brute force detection:
index=wineventlog EventCode=4625
| stats count by Account_Name, IpAddress
| sort - count

Results & Findings
• 	Successfully ingested Sysmon and Windows logs
• 	Detected multiple attack patterns from Kali Linux
• 	Built custom SPL detections
• 	Investigated alerts end‑to‑end
• 	Improved understanding of endpoint telemetry and SOC workflows

