# 🖥️ Windows Endpoint SOC Log Analysis (Advanced)

## Project Objective
To simulate a real-world SOC investigation on a Windows endpoint by analyzing authentication events, post-authentication process execution, and audit visibility limitations to identify suspicious behavior such as brute-force attempts and encoded PowerShell execution.

---

## Environment
- **Operating System:** Windows (Home Edition)
- **Log Source:** Windows Security Event Logs
- **Analysis Tool:** Windows Event Viewer
- **User Context:** Local user account

---

## Events Analyzed
- **4625** – Failed logon  
- **4624** – Successful logon  
- **4688** – Process creation  
- **7045** – Service installation (attempted, not logged due to audit limitation)

---

## Incident Timeline

### T1 – Repeated Authentication Failures
Multiple **Event ID 4625 (Failed Logon)** events were observed for the local account **SRIRAAM** within a short time window. The failures occurred in rapid succession, indicating repeated authentication attempts rather than an isolated user error. This pattern is consistent with a **potential brute-force or credential-guessing attempt**.

---

### T2 – Successful Authentication
Following the failed attempts, a **successful logon (Event ID 4624)** was recorded for the same local user account **SRIRAAM**. The proximity of the successful logon to the repeated failures suggests successful access after multiple authentication attempts.

---

### T3 – Post-Authentication Suspicious Execution
After the successful authentication, **Event ID 4688 (Process Creation)** recorded the execution of **`powershell.exe`** with the `-EncodedCommand` parameter. Encoded PowerShell execution is a **high-signal behavior** often associated with obfuscation techniques and is commonly investigated by SOC teams as potential post-compromise activity.

---

### T4 – Persistence Attempt (Simulated)
A persistence mechanism was simulated using the `sc create` command to install a new service. However, no corresponding **Event ID 7045 (Service Installation)** was generated despite enabling relevant audit policies. This indicates an **audit visibility limitation on Windows Home systems**, where certain persistence-related events may not be logged to the Security event log.

---

## SOC Analysis & Verdict
The observed activity represents a **simulated credential abuse scenario** in which repeated authentication failures were followed by a successful logon and suspicious post-authentication PowerShell execution.

Encoded PowerShell usage immediately following authentication is considered a **high-risk indicator** in SOC investigations due to its frequent use in obfuscated attacker workflows. While a persistence mechanism was simulated, the absence of Event ID 7045 highlights a logging visibility gap rather than confirmation or denial of persistence.

**Verdict:**  
Suspicious activity consistent with **brute-force authentication followed by potentially malicious post-authentication execution**. No evidence of lateral movement, payload execution, or external command-and-control communication was observed.

---

## MITRE ATT&CK Mapping
- **T1110 – Brute Force**  
  Repeated failed authentication attempts (Event ID 4625).

- **T1059 – Command and Scripting Interpreter (PowerShell)**  
  Encoded PowerShell execution observed via Event ID 4688.

- **T1543 – Create or Modify System Process (Simulated)**  
  Persistence simulated via service creation; corresponding event not logged due to audit limitations.

---

## Audit Visibility Limitation
Service creation was simulated using the `sc create` command; however, **Event ID 7045 was not generated** despite enabling Security System Extension auditing. This behavior is consistent with known limitations of Windows Home editions.

In a production environment, this visibility gap would be mitigated using **Windows Pro audit policies** or **Endpoint Detection and Response (EDR)** telemetry to ensure persistence mechanisms are reliably captured.

---

## Severity Assessment
- **Severity (Lab Environment):** Low  
- **Potential Severity (Production):** Medium to High  

The observed behavior would warrant escalation in a production environment due to the combination of credential abuse and suspicious post-authentication execution.

---

## SOC Recommendations
- Monitor and alert on **repeated failed authentication attempts** targeting the same user account.
- Correlate **failed logons (4625)** with subsequent **successful logons (4624)**.
- Alert on **encoded PowerShell execution** (Event ID 4688 with `-EncodedCommand`).
- Harden endpoint audit policies or deploy **EDR solutions** to improve visibility into persistence mechanisms.
- Enforce **account lockout policies** and strong password requirements to reduce brute-force risk.

---

## Outcome
This project demonstrates **advanced Windows endpoint SOC analysis**, including authentication abuse detection, post-authentication behavior analysis, audit policy configuration, and identification of logging visibility gaps. The investigation follows a realistic SOC workflow of **detect → analyze → assess → document**, reflecting real-world blue team operations.

---

## Skills Demonstrated
- Windows Security Event Log analysis  
- SOC incident investigation and documentation  
- Authentication abuse detection  
- PowerShell execution analysis  
- MITRE ATT&CK mapping  
- Audit policy configuration and visibility assessment  
