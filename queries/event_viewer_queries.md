# Event Viewer Investigation Queries

This document contains the queries and filtering techniques used to investigate authentication activity during the simulated security incident.

---

## Failed Login Attempts

SOC analysts typically begin by identifying repeated authentication failures.

Event ID:
4625

Meaning:
Failed login attempt.

Event Viewer Filter Used:

Event Viewer → Windows Logs → Security → Filter Current Log

Event ID:
4625

Purpose:
Identify brute force attempts or incorrect login attempts against domain accounts.

---

## Successful Login

Event ID:
4624

Meaning:
Successful authentication.

Purpose:
Determine whether an attacker eventually gained access after multiple failures.

This event helps confirm if login attempts eventually succeeded.

---

## Password Reset Activity

Event ID:
4724

Meaning:
An attempt was made to reset a user's password.

Purpose:
Detect account takeover or administrative password resets.

In this lab, the password for the account **alex.support** was reset by the domain administrator.

---

## Investigation Method

1. Identify multiple **4625 failed logins**
2. Look for a **4624 successful login**
3. Identify **4724 password reset activity**

This sequence can indicate:

• brute force attempts  
• account compromise  
• administrative intervention

---

## Key Observation

In this lab investigation the following activity was identified:

Multiple failed login attempts targeting **alex.support**, followed by account activity and an administrative password reset.

This sequence demonstrates how authentication logs can reveal suspicious activity and assist SOC analysts during incident investigation.
