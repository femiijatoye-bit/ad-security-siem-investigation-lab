# Lessons Learned

## Security Event Correlation

This lab demonstrated how multiple Windows Security Events can be correlated to understand suspicious activity within an Active Directory environment.

Key events analyzed:

- **Event ID 4625** — Failed Logon Attempt
- **Event ID 4624** — Successful Logon
- **Event ID 4724** — Password Reset Attempt

These events help security analysts detect authentication abuse, brute force attempts, and administrative account actions.

---

## Failed Authentication Detection

Repeated **Event ID 4625** entries indicate multiple authentication failures against a specific account.

This pattern may indicate:

- Password guessing
- Brute force attempts
- Incorrect credential usage

Monitoring repeated authentication failures is critical for early detection of potential account compromise.

---

## Administrative Actions

Administrative actions such as password resets generate:

```
Event ID 4724
```

This event is useful for tracking:

- Account recovery
- Privileged account activity
- Potential unauthorized administrative actions

Monitoring these events helps ensure that privileged operations are legitimate.

---

## SOC Investigation Workflow

This lab reinforced the importance of the following investigation process:

1. Identify suspicious authentication patterns
2. Correlate related security events
3. Investigate administrative account activity
4. Determine whether the behavior represents malicious activity or legitimate intervention

---

## Key Takeaway

Windows Security Event Logs provide valuable forensic evidence that enables SOC analysts to reconstruct authentication activity and identify suspicious patterns within enterprise environments.
