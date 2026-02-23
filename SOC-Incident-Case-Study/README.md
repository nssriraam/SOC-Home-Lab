# SOC Incident Case Study – Suspicious Authentication & Execution Activity

## Incident Overview

This case study documents a simulated Security Operations Center (SOC) investigation into suspicious authentication activity followed by potentially malicious post-authentication behavior on a Windows endpoint.

The objective of this case study is to demonstrate a real-world SOC analyst workflow, covering alert triage, investigation, severity assessment, response actions, documentation, and case closure.

---

## Initial Alert

The investigation was initiated after detecting multiple failed authentication attempts targeting a single user account within a short time window.

The alert was escalated when a successful authentication occurred shortly after the failures, followed by suspicious PowerShell execution involving encoded commands. This sequence is commonly associated with credential abuse and post-authentication malicious activity.

---

## Alert Triage

Initial triage was performed to assess whether the activity aligned with normal user behavior or indicated potential malicious intent.

The following aspects were reviewed:
- Frequency and timing of authentication failures
- Affected user account and endpoint
- Correlation between authentication and execution events

The observed behavior deviated from normal patterns, requiring further investigation.

---

## Investigation & Analysis

A detailed investigation was conducted by correlating authentication logs and endpoint execution telemetry.

Investigation steps included:
- Reviewing authentication activity before and after the alert timestamp
- Identifying repeated login failures followed by a successful login
- Analyzing PowerShell execution events for suspicious indicators
- Evaluating the use of encoded commands, commonly associated with malicious execution

The close timing between authentication success and suspicious execution increased the likelihood of credential compromise.

---

## Severity Assessment

Based on the investigation findings, the incident was classified as **Medium to High severity** due to:
- Evidence of repeated authentication failures
- Successful access following failed attempts
- Suspicious post-authentication command execution

While full system compromise was not confirmed, the behavior posed a notable security risk.

---

## Response Actions

Response actions were initiated in accordance with SOC procedures, including:
- Enhanced monitoring of the affected user account
- Review of recent endpoint and account activity
- Recommendation for credential reset
- Advising endpoint inspection and further threat hunting activities

These actions aimed to minimize potential impact and prevent further misuse.

---

## Documentation & Case Closure

All investigation steps, findings, and response actions were documented within the case record for audit and future reference.

After confirming that no additional suspicious activity was observed and no further indicators of compromise were detected, the incident was formally closed with appropriate justification.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | Description |
|------|----------|------------|
| Credential Access | Brute Force (T1110) | Multiple failed authentication attempts observed |
| Execution | PowerShell (T1059.001) | Encoded PowerShell commands executed post-authentication |

---

## Analyst Notes

- Failed authentication attempts followed by successful access is a common indicator of credential compromise.
- Encoded PowerShell execution significantly increases the likelihood of malicious intent.
- No evidence of lateral movement or persistence was identified during the investigation.

---

## Outcome

- No confirmed system compromise detected
- Potential credential misuse contained through monitoring and response
- Recommendations provided to reduce future security risk

---

## Skills Demonstrated

- SOC alert triage and validation
- Log correlation and investigation
- Incident severity classification
- Response decision-making
- Professional SOC documentation and case handling

---

**This case study demonstrates practical SOC analyst skills and complements endpoint detection projects by showcasing incident response and investigative workflows.**
