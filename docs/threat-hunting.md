# Threat Hunting

## Overview

Threat hunting was performed using the Wazuh Dashboard to investigate security events generated during attack simulations.

The objective was to identify suspicious activity, validate detections, and analyze event details collected from the monitored Windows endpoint.

---

## Hunt 1: User Account Creation Activity

### Goal

Identify newly created user accounts.

### Indicators

* Event ID 4720
* User account creation activity
* Account creation timestamp
* User responsible for the action

### Investigation Steps

1. Search for Event ID 4720.
2. Review the created username.
3. Verify the initiating account.
4. Confirm the event source.

### Findings

The simulated attacker account creation was successfully detected and logged by Wazuh.

---

## Hunt 2: Administrator Group Membership Changes

### Goal

Identify privilege escalation activity.

### Indicators

* Event ID 4732
* Administrator group modifications
* User added to privileged groups

### Investigation Steps

1. Search for Event ID 4732.
2. Identify the affected group.
3. Review the user added to the group.
4. Verify the initiating account.

### Findings

Privilege escalation activity was successfully detected and logged by Wazuh.

---

## Hunt 3: File Integrity Monitoring Events

### Goal

Identify unauthorized file modifications.

### Indicators

* File creation events
* File modification events
* File deletion events

### Investigation Steps

1. Review FIM alerts.
2. Identify affected files.
3. Compare timestamps.
4. Validate whether the activity was authorized.

### Findings

File creation and modification activities generated alerts as expected.

---