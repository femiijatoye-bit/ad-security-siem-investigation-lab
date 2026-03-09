# Active Directory Security SIEM Investigation Lab

## Overview

This lab simulates common authentication and account-management events within an Active Directory environment and demonstrates how a SOC analyst investigates suspicious activity using Windows Event Viewer.

The objective of this lab was to generate and analyze security events associated with:

- Failed authentication attempts
- Successful logon activity
- Administrative password reset actions

By correlating these events, the lab demonstrates how analysts identify potential brute force attempts and investigate account-related security activity.

---

# Key Skills Demonstrated

- Windows Event Log Analysis
- Active Directory Account Management
- Security Event Correlation
- Authentication Investigation
- SOC Incident Analysis Workflow

---

# Lab Environment

| Component | Description |
|---|---|
| Host System | macOS (M1 MacBook Air) |
| Virtualization | UTM |
| Domain Controller | Windows Server (Active Directory) |
| Domain | corp.local |
| Tools Used | Event Viewer, Active Directory Users and Computers |

---

# Lab Objectives

- Simulate authentication failures against a domain user account
- Analyze Windows Security Event Logs
- Identify failed logon patterns
- Investigate successful authentication events
- Track administrative account actions
- Practice SOC investigation methodology

---

# Attack Simulation

## Step 1 — Failed Login Attempts

Multiple failed login attempts were performed against the account:

```
corp\alex.support
```

Incorrect passwords were entered several times to simulate credential guessing activity.

This generated the following security event:

```
Event ID 4625 — Failed Logon
```

Evidence captured:

- `01_failed_logon_event_4625.png`
- `10_multiple_failed_logons_event_4625_sequence.png`

---

## Step 2 — Successful Logon Event

After failed login attempts, authentication activity was reviewed to identify successful logon events.

This generated:

```
Event ID 4624 — Successful Logon
```

Evidence captured:

- `02_successful_logon_event_4624.png`

---

## Step 3 — Administrative Password Reset

An administrative account performed a password reset on the user account:

```
alex.support
```

This generated the following security event:

```
Event ID 4724 — Attempted Password Reset
```

Evidence captured:

- `08_ad_password_reset_confirmation.png`
- `09_event_4724_password_reset_alex_support.png`

---

# Security Event Analysis

During investigation, the following event pattern was identified:

| Event ID | Description |
|---|---|
| 4625 | Failed authentication attempts |
| 4624 | Successful logon |
| 4724 | Administrative password reset |

This sequence is commonly associated with:

- Credential guessing attempts
- Brute force authentication attempts
- Account recovery actions by administrators

---

# Investigation Process

A SOC analyst reviewing these logs would typically perform the following steps:

1. Identify repeated authentication failures (Event ID 4625)
2. Correlate timestamps between authentication events
3. Identify successful logon events following failures
4. Review administrative actions affecting the account
5. Determine whether activity represents malicious behavior or legitimate administrative intervention

---

# Response Actions

Based on investigation findings, the following response actions were taken:

- Account password reset performed by administrator
- Authentication activity reviewed in Security logs
- Continued monitoring recommended for suspicious login attempts

---

# Evidence

```
evidence/

01_failed_logon_event_4625.png
02_successful_logon_event_4624.png
08_ad_password_reset_confirmation.png
09_event_4724_password_reset_alex_support.png
10_multiple_failed_logons_event_4625_sequence.png
```


---

# Key Takeaways

This lab demonstrates how security analysts detect suspicious authentication activity by correlating Windows security events. Monitoring failed logon attempts and administrative actions provides valuable insight into potential brute force activity and account compromise attempts.

---
# Author

Femi Ijatoye  
Security+ Certified  
Cybersecurity / SOC Analyst Portfolio Project
