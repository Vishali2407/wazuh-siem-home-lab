# Detection Scenarios

## 1. User Account Creation Detection

### Objective

Detect unauthorized creation of local user accounts.

### Attack Simulation

```cmd
net user attacker Password@123 /add
```

### Event Generated

* Event ID: 4720

### MITRE ATT&CK

* T1136 - Create Account

### Evidence

* User creation command
* Wazuh alert
* Event details

---

## 2. Administrator Group Membership Detection

### Objective

Detect privilege escalation through administrator group assignment.

### Attack Simulation

```cmd
net localgroup Administrators attacker /add
```

### Event Generated

* Event ID: 4732

### MITRE ATT&CK

* T1098 - Account Manipulation

### Evidence

* Administrator group modification command
* Wazuh alert
* Event details

---

## 3. File Integrity Monitoring (FIM)

### Objective

Detect unauthorized file modifications.

### Detection Logic

Wazuh Syscheck monitors protected files and directories and generates alerts when files are:

* Created
* Modified
* Deleted

### Evidence

* File creation event
* File modification event
* Wazuh FIM alert

---

## 4. Registry Monitoring

### Objective

Detect registry modifications that may indicate persistence or configuration tampering.

### Detection Logic

Wazuh continuously monitors configured Windows registry locations and generates alerts when changes occur.
