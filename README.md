# 🛡️ My Home SOC Lab Project

## A hands‑on Security Operations Center home lab built using Splunk, Windows 10, Kali Linux, Sysmon, and real attack simulations.

## 📌 Table of Contents

* Overview
* Architecture
* Objectives
* Tools & Technologies
* Lab Topology
* Deployment Steps
* VirtualBox Environment Setup
* Splunk Enterprise Installation
* Universal Forwarder Setup
* Sysmon Deployment
* Data Onboarding in Splunk
* Kali Linux Attack Simulation
* Detection Engineering (SPL)
* Incident Investigation
* Splunk Searches
* Results & Findings
* Future Improvements

# 🧭 Overview
This project documents the creation of a complete SOC Home Lab using VirtualBox, Splunk Enterprise, Windows 10, Kali Linux, and Sysmon.
The goal is to simulate real‑world SOC workflows including log ingestion, detection engineering, threat simulation, and incident investigation.

# 🏗️ Architecture
## Components:
*   VirtualBox hypervisor
* 	Windows 10 VM (monitored endpoint)
*   Kali Linux VM (attacker machine)
*   Splunk Enterprise Server
* 	Splunk Universal Forwarder
* 	Sysmon for detailed endpoint telemetry

# 🎯 Objectives
* 	Build a functional SOC environment
* 	Collect and analyze Windows logs using Splunk
* 	Deploy Sysmon for high‑fidelity telemetry
* 	Simulate real‑world attacks from Kali Linux
* 	Create SPL‑based detections
* 	Investigate suspicious activity end‑to‑end
* 	Document findings and lessons learned

# 🧭 Overview
* This project documents the creation of a complete SOC Home Lab using VirtualBox, Splunk Enterprise, Windows 10, Kali Linux, and Sysmon.
* The goal is to simulate real‑world SOC workflows including log ingestion, detection engineering, threat simulation, and incident investigation.

# 🛠️ Tools & Technologies
* Virtualisation = VirtualBox
* SIEM = Splunk Enterprise
* Endpoint = Windows 10
* Attacker = Kali Linux
* Logging = Sysmon, Windows Event Logs
* Forwarding = Splunk Universal Forwarder
* Simulation = Nmap, Metasploit, Powershell abuse, Hydra
* Analysis = SPL, Dashboards, Alerts

# 🚀 Deployment Steps
## VirtualBox Environment Setup
* Installed VirtualBox
* Created Windows 10 VM
* Created Kali Linux VM
* Configured host-only netowrking for isolated traffic

## Splunk Enterprise Installation
* Installed Splunk on Windows
* Configured admin credentials
* Enabled receiving on port 9997
* Verified Splunk Web access

## Universal Forwarder Setup
* Installed Splunk universal forwarder on Windows 10
* Configured forwarding to Splunk server
* Verified connection using: splunk list forward-server

## Data Onboarding in Splunk
* Onboarded:
* Sysmon logs
* Security logs
* Powershell logs
* Application logs
* Verified logs in:
* index=wineventlog
* index=sysmon

  ## Kali Linux Attack Simulation
  * Simulated attacks included:
  * Nmap scanning
  * Brute force attempts(Hydra)
  * Malware exe file creation in Kali linux
  * Powershell exploitation

  ## Detection Engineering (SPL)
  * Created SPL Alerts for:
  * Suspicious Pwershell commands
  * Sysmon Event ID 1 anomalies
  * Multiple failed logons
  * Reverse shell behaviour
  * Network scanning patterns
 
  ## Incident Investigation
  * Documented:
  * Alerts triggered
  * Timeline of events
  * Affected user and host
  * Root cause analysis
  * Response actions taken

## Splunk searches
* Spl
* index=sysmon EventCode=1
* | search Image="*powershell.exe"
* | stats count by CommandLine, ParentImage, Computer

* Network Scanning Detection
* Spl
* index=sysmon EventCode=3
* | stats count by DestinationIp, DestinationPort
* | where count > 50

# Results/Findings
* Successfully ingested Sysmon and Windows logs
* Detected multiple attack patterns from Kali linux
* Built custom SPL detections
* Investigated alerts end-to-end
* Improved understanding of endpoint telemetry and SOC workflows
