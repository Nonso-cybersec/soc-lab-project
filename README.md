
# Wazuh SIEM SOC Monitoring Lab (VirtualBox)

## Project Overview
This project demonstrates a complete SOC environment using Wazuh SIEM to monitor Windows and Linux endpoints, detect security events, and simulate attacker behavior using Kali Linux.



## Objectives

* Deploy a centralized SIEM using Wazuh
* Monitor Windows and Linux endpoints
* Generate security events using Kali Linux
* Analyze alerts and logs within the Wazuh dashboard
* Simulated real-world SOC monitoring, log analysis, and intrusion detection scenarios

## Lab Architecture

### Virtual Machines

| System       | Role                                    |
| ------------ | --------------------------------------- |
| Ubuntu 24.04 | Wazuh Manager, Indexer, Dashboard       |
| Windows Server 2019     | Monitored Endpoint (Wazuh Agent)        |
| Kali Linux   | Attacker Machine and Monitored Endpoint |


### Network Configuration

* VirtualBox NAT Network
* All VMs connected to the same virtual network
* Wazuh Manager IP: 10.0.2.4

## Wazuh Installation

### Ubuntu Server

Downloaded and executed the Wazuh installation assistant:

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```

### Challenges Encountered

* Existing Wazuh agent conflicted with manager installation
* Broken package removal scripts
* Wazuh manager startup timeout
* API connection issues
* VirtualBox network configuration troubleshooting

### Resolutions

* Removed existing Wazuh agent
* Repaired package database using dpkg and apt
* Increased VM memory from 4 GB to 6 GB
* Restarted Wazuh services
* Simplified networking by using a single NAT Network adapter

## Agent Deployment

### Kali Linux Agent

Installed and connected successfully to the Wazuh Manager.

Status: Active

### Windows Agent

Installed using the Wazuh MSI package.

Manager IP:

```text
10.0.2.4
```

Service:

```powershell
Start-Service WazuhSvc
```

Status: Active

## Results

Successfully deployed:

* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard
* Kali Agent
* Windows Agent

All agents connected and reporting successfully.

## Skills Demonstrated

* SIEM Deployment
* Security Monitoring
* Linux Administration
* Windows Endpoint Monitoring
* VirtualBox Networking
* Wazuh Agent Management
* Troubleshooting and Incident Resolution
* SOC Lab Design

## Future Enhancements

* Sysmon integration
* Suricata integration
* Nmap detection use cases
* Brute-force attack detection
* Custom Wazuh rules
* Threat hunting exercises

### Wazuh Dashboard - Active Agents

![Wazuh Dashboard](images/wazuh.png)

This shows successful connection of Windows and Kali agents to the Wazuh SIEM.


* Wazuh Dashboard
* Agent Summary
* Active Agents
* Security Events
* Lab Architecture Diagram

 ## Detection Scenarios Simulated

- Port scanning (Kali → Windows)
- Authentication failures (Windows)
- Endpoint log monitoring (Kali & Windows)
- Security event correlation in Wazuh SIEM

- ## SOC Attack Simulation: Hidden Process Detection

## Objective

This project demonstrates how hidden processes and rootkit-like behavior can be detected using Wazuh rootcheck monitoring on a Linux endpoint.

The goal is to simulate stealth techniques and observe how a SIEM detects anomalous activity.

---


## Lab Environment

- Ubuntu Linux (Wazuh Agent installed)
- Wazuh Manager (SIEM Dashboard)
- Kali Linux (optional attacker VM)

---

## Step 1: System Preparation (Ubuntu Endpoint)

Switch to root and update system packages:

```bash

sudo -i

apt update

```

## Detection Results — June 10, 2026

### Alert Triggered
After loading Diamorphine and hiding rsyslogd (PID 812),
Wazuh rootcheck detected the hidden process within minutes.

### Alert Details
- **Rule ID:** 521
- **Rule Level:** 11 (High Severity)
- **MITRE ATT&CK:** T1014 — Rootkit
- **Tactic:** Defense Evasion
- **Detection Message:** Process '812' hidden from /proc. 
  Possible kernel level rootkit.
- **Fired Times:** 4

### How Wazuh Detected It
Wazuh rootcheck independently scans /proc and compares 
what the kernel reports against actual running processes.
A mismatch between the two = hidden process = rootkit alert.

### Key Takeaway
Kernel rootkits hide from the OS itself but cannot hide 
from a SIEM doing independent out-of-band verification.
This is why endpoint monitoring is critical — the OS 
cannot be trusted when compromised at kernel level.

### Wazuh Dashboard - Active Agents
![Wazuh Dashboard](images/wazuh-dashboard-agents.png)

### Rootkit Detection Alert
![Rootkit Detection](images/rootkit.png)

### Kernel Rootkit Logs
![Kernel Rootkit Logs](images/kernel%20Rootkit%20Logs.png)
