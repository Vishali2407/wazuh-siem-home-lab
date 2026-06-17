# Troubleshooting

## Overview

During the deployment and testing of the Wazuh SIEM home lab, several issues were encountered and resolved.

This document records the problems, root causes, troubleshooting steps, and resolutions.

---

## Issue 1: Wazuh Agent Connectivity Problem

### Problem

The Windows Wazuh Agent became disconnected from the Wazuh Manager.

### Symptoms

* Agent displayed as disconnected
* No new alerts generated
* Agent status showed offline

### Root Cause

Network communication between the Wazuh Agent and Wazuh Manager was interrupted.

### Resolution

Verified:

* Agent service status
* Manager service status
* Network connectivity
* Firewall rules

Required ports were opened:

* 1514/TCP
* 1515/TCP
* 443/TCP

### Result

The agent successfully reconnected to the manager.

---

## Issue 2: PowerShell Event ID 4104 Not Generated

### Problem

PowerShell commands were executed but Event ID 4104 logs were not generated.

### Symptoms

* No Script Block Logging events
* No PowerShell detection alerts

### Root Cause

PowerShell Script Block Logging was not enabled.

### Resolution

Enabled Script Block Logging through Windows registry configuration and verified logging through Event Viewer.

### Result

Event ID 4104 events were successfully generated.

---

## Issue 3: PowerShell Detection Rule Not Triggering

### Problem

PowerShell events existed but no Wazuh alerts were generated.

### Symptoms

* Event ID 4104 visible in Windows logs
* No corresponding Wazuh alert

### Root Cause

A custom detection rule was not configured.

### Resolution

Created a custom Wazuh rule in:

```text
rules/local_rules.xml
```

Restarted the Wazuh Manager and validated alert generation.

### Result

PowerShell execution activity successfully generated alerts.

---

## Lessons Learned

* Verify endpoint logging before troubleshooting detections.
* Validate agent connectivity before investigating missing alerts.
* Test custom rules after deployment.
* Confirm firewall configuration when connectivity issues occur.
* Use Event Viewer to validate Windows event generation before analyzing Wazuh alerts.
