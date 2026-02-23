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

# 🌐 Lab Topology
* +-------------------+         +---------------------------+
* | Windows 10 VM     | ----->  | Splunk Universal Forwarder |
* | Sysmon + EventLog |         | (Log Forwarding)           |
* +-------------------+         +---------------------------+
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



