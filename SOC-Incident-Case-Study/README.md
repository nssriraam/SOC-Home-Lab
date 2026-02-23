# SOC Incident Case Study – Suspicious Authentication & Execution Activity

## Incident Overview
This case study documents a simulated SOC investigation into suspicious authentication activity followed by potentially malicious post-authentication behavior. The investigation demonstrates how a SOC analyst correlates endpoint authentication logs and execution telemetry to determine incident severity and response.

---

## Initial Alert
The investigation was initiated after identifying **multiple failed authentication attempts** targeting a single user account within a short time window. The alert was further escalated due to a **successful authentication occurring shortly after the failures**, followed by **suspicious PowerShell execution using encoded commands**.

Such a sequence is commonly monitored by SOC teams as it may indicate credential abuse followed by post-authentication activity.
