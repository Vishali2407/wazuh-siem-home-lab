# Lab Architecture

## Overview

This project implements a Security Information and Event Management (SIEM) home lab using Wazuh to collect, analyze, and monitor security events generated from a Windows 11 endpoint.

The lab was designed to simulate a basic Security Operations Center (SOC) environment and demonstrate security monitoring, detection engineering, and incident investigation capabilities.

---

## Components

### Windows 11 Endpoint

The Windows 11 system acts as the monitored endpoint.

Responsibilities:

* Generate Windows Security Events
* Generate PowerShell Events
* Generate File Integrity Monitoring (FIM) Events
* Generate Registry Modification Events
* Forward logs through the Wazuh Agent

---

### Wazuh Agent

The Wazuh Agent is installed on the Windows endpoint.

Responsibilities:

* Collect endpoint telemetry
* Monitor Windows Event Logs
* Monitor File Integrity Changes
* Monitor Registry Changes
* Send security events to the Wazuh Manager

---

### Wazuh Manager

The Wazuh Manager is installed on Ubuntu Server.

Responsibilities:

* Receive events from agents
* Decode and normalize logs
* Apply detection rules
* Generate security alerts
* Map alerts to MITRE ATT&CK techniques

---

### OpenSearch Indexer

The OpenSearch Indexer stores collected security events.

Responsibilities:

* Store log data
* Index alerts
* Enable fast searches
* Support dashboard visualization

---

### Wazuh Dashboard

The Wazuh Dashboard provides a graphical interface for monitoring and investigation.

Responsibilities:

* Display alerts
* Visualize security events
* Support threat hunting
* Enable incident investigation

---

## Data Flow

```text
Windows 11 Endpoint
        │
        ▼
Wazuh Agent
        │
        ▼
Ubuntu Wazuh Manager
        │
        ▼
OpenSearch Indexer
        │
        ▼
Wazuh Dashboard
```

---

## Architecture Screenshot

Add the architecture diagram screenshot in:

screenshots/architecture/lab-architecture.png

---

## Security Monitoring Capabilities

The architecture supports:

* User Account Monitoring
* Privileged Group Monitoring
* File Integrity Monitoring (FIM)
* Registry Monitoring
* PowerShell Monitoring
* Alert Generation
* Threat Hunting
* Incident Investigation
