# ICS-RedSim: SCADA / ICS Attack Simulation Framework

A **virtual Industrial Control System (ICS) cybersecurity lab** designed to simulate SCADA security incidents in a safe and controlled environment.
This project builds a **mini industrial plant simulation** using OpenPLC and FUXA and evaluates security detection mechanisms using Suricata IDS, Wazuh, and Wireshark.

The lab enables testing of **industrial cyber attack scenarios**, monitoring abnormal behavior, and validating detection techniques without using real industrial hardware.

---

# Project Overview

Industrial Control Systems (ICS) are widely used in critical infrastructure such as power plants, manufacturing industries, and water treatment facilities. These systems are increasingly connected to IT networks, making them vulnerable to cyber threats.

ICS-RedSim provides a **low-cost virtual ICS security testing environment** where common industrial attack scenarios can be simulated and monitored.

Key objectives of the project:

* Build a **virtual SCADA/ICS environment**
* Simulate **industrial security incidents**
* Monitor traffic and logs using **IDS and SIEM tools**
* Validate detection of abnormal ICS behavior
* Collect evidence for analysis and reporting

---

# System Architecture

The lab environment is divided into multiple security zones similar to real industrial networks.

| Zone                | Components                       |
| ------------------- | -------------------------------- |
| IT Zone             | Analyst workstation              |
| DMZ Monitoring Zone | Suricata IDS + Wazuh             |
| OT Zone             | OpenPLC (PLC) + FUXA (SCADA/HMI) |
| Test/Attacker Zone  | Kali Linux for simulation        |

Communication between SCADA and PLC occurs using **Modbus/TCP**, a commonly used industrial protocol.

---

# Technologies Used

| Tool               | Purpose                                  |
| ------------------ | ---------------------------------------- |
| OpenPLC            | PLC logic simulation                     |
| FUXA               | SCADA/HMI dashboard                      |
| Suricata           | Intrusion Detection System               |
| Wazuh              | Security monitoring and SIEM             |
| Wireshark          | Network packet analysis                  |
| VMware Workstation | Virtual lab environment                  |
| Kali Linux         | Security testing and scenario simulation |

---

# Network Architecture

Example IP plan used in the lab:

| Device        | IP Address    | Role               |
| ------------- | ------------- | ------------------ |
| PLC VM        | 192.168.x.x | OpenPLC Controller |
| SCADA VM      | 192.168.x.x | FUXA HMI           |
| Monitoring VM | 192.168.x.x | Suricata + Wazuh   |
| Attacker VM   | 192.168.x.x | Kali Linux         |

---

# ICS Process Simulation

A simple **industrial tank control system** was implemented.

Process features include:

* Pump start/stop control
* Tank level monitoring
* Automatic high-level alarm
* Real-time SCADA dashboard visualization
* Modbus register communication between PLC and SCADA

---

# Security Monitoring

Network and host monitoring were implemented using:

**Suricata IDS**

* Detects abnormal network activity
* Generates alerts for suspicious Modbus traffic

**Wazuh**

* Collects logs from Suricata
* Provides centralized monitoring dashboard

**Wireshark**

* Captures baseline network traffic
* Analyzes Modbus communication patterns

---

# Simulation Scenarios

Multiple security scenarios were executed to validate detection capability.

### Category A — Discovery and Misuse

| Scenario | Description                       |
| -------- | --------------------------------- |
| A1       | OT Network Scan Attempt           |
| A2       | Unauthorized Modbus Read Burst    |
| A3       | Unauthorized Modbus Write Attempt |

### Category B — Process Integrity

| Scenario | Description                  |
| -------- | ---------------------------- |
| B1       | Sensor Spoofing Simulation   |
| B2       | Rapid Command Timing Anomaly |

### Category C — Availability Attacks

| Scenario | Description              |
| -------- | ------------------------ |
| C1       | Traffic Flood Simulation |
| C2       | SCADA Service Disruption |

### Category D — Detection Validation

| Scenario | Description                           |
| -------- | ------------------------------------- |
| D1       | IDS Alert Verification                |
| D2       | Incident Response Evidence Collection |

---

# Baseline Traffic Analysis

Normal industrial traffic patterns were captured using Wireshark.

Baseline observations include:

* Periodic Modbus polling between SCADA and PLC
* Low network traffic volume
* Predictable communication intervals
* No unknown hosts communicating with OT devices

This baseline helps identify abnormal behavior during simulated incidents.

---

# Detection Results

During simulation scenarios:

* Suricata successfully detected suspicious network activity
* Wazuh dashboard displayed security alerts
* Wireshark captured abnormal packet patterns

The lab demonstrates how **industrial intrusion detection can identify abnormal ICS behavior**.

---

# Repository Structure

```
ICS-RedSim-SCADA-Attack-Simulation-Lab
│
├── docs
│   ├── architecture
│   └── report
│
├── plc
│   └── ladder-logic
│
├── scada
│   └── dashboard
│
├── monitoring
│   ├── suricata
│   ├── wazuh
│   └── wireshark
│
├── scenarios
│
├── evidence
│   ├── pcaps
│   ├── logs
│   └── screenshots
│
└── demo
```

---

# Demo

The demonstration shows the complete workflow:

1. Normal industrial process operation
2. Security incident simulation
3. Detection using IDS
4. Evidence collection and analysis

Screenshots and demonstration video are included in the repository.

---

# Limitations

* The environment is fully virtualized and does not include physical PLC hardware.
* Only Modbus/TCP protocol is simulated.
* Advanced ICS protocols such as DNP3 or OPC UA are not included.

---

# Future Improvements

Possible extensions of this project include:

* Integration with real PLC hardware
* Support for additional ICS protocols
* Machine learning-based anomaly detection
* Automated incident response mechanisms

---

# Author

Om Asutosh Das
B.Tech Student – Cybersecurity & Cyberdefense
Sri Sri University

---
