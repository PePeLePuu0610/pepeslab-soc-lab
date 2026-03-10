# pepeslab-soc-lab
# Project: Virtualized SOC & Detection Engineering Lab
A comprehensive environment designed for simulating cyber attacks, capturing telemetry, and developing high-fidelity detections.
## 📌 Project Overview
This repository contains the architecture, configuration, and detection logic for my home SOC lab. The goal of this project is to bridge the gap between "attacker behavior" and "defender visibility" by mapping real-world exploits to actionable SIEM alerts.
## 🏗️ Architecture
- **Hypervisor:** VMware ESXi / Workstation
- **SIEM/Analytics:** Splunk Enterprise
- **Endpoint Protection:** Wazuh (EDR/HIDS) & Sysmon
- **Firewall/Routing:** pfSense
- **Endpoints:** Windows Server 2022 (AD), Windows 10, Ubuntu 22.04
## 📂 Repository Structure
* `build/`: Documentation for network interfaces, IP schema, and VM configurations.
* `scripts/`: Python and PowerShell tools for traffic generation and attack simulation.
* `telemetry/`: Sample logs (JSON/CSV) captured during simulated attack phases.
* `detections/`: Production-ready Splunk SPL and Wazuh XML rules.
## 🚀 Lab Use Cases
### 1. Brute Force Detection
**Scenario:** A remote attacker attempts to guess SSH credentials via a wordlist attack.
- **Generator:** `scripts/brute_force_gen.py`
- **Detection Logic:** Identifying >5 failures within 2 minutes followed by a successful login from the same source IP.
- **Query:** [Link to detections/SPL/brute_force.spl]
### 2. Living off the Land (LotL)
**Scenario:** Using `certutil.exe` to download malicious payloads.
- **Telemetry Source:** Windows Event ID 4688 (Process Creation)
- **Detection:** Monitoring for command-line arguments containing "urlcache" or "split".
## 🛠️ How to Use This Repo
1. Follow the `build/` guide to set up your virtual network.
2. Run the simulation scripts in `scripts/` to generate telemetry.
3. Ingest the logs into Splunk and apply the queries found in `detections/`.
##Continue Editing here
<img width="691" height="557" alt="image" src="https://github.com/user-attachments/assets/963992fe-da09-49a6-bc30-84c2e3ba630b" />
