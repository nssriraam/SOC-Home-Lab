# Windows Endpoint SOC Log Analysis

## 🎯 Objective

Analyze Windows Security Event Logs to identify suspicious authentication behavior and simulate how a SOC analyst detects brute-force login attempts on endpoints.

---

## 🧪 Environment

* Operating System: Windows
* Log Source: Windows Security Event Logs
* Tool Used: Event Viewer

---

## 🔍 Events Analyzed

* **Event ID 4625** – Failed logon
* **Event ID 4624** – Successful logon

---

## 🔁 Activity Performed

* Generated multiple failed login attempts using incorrect credentials within a short time window
* Analyzed authentication logs focusing on:

  * Account name
  * Logon type
  * Failure reason
  * Timestamps
* Compared failed logon events with a subsequent successful logon to assess risk

---

## 📊 Findings

* Multiple failed authentication attempts occurred for the same account within minutes
* Failures followed a consistent logon pattern
* A successful login occurred after repeated failures, increasing the potential risk level

---

## 🧠 SOC Analysis & Interpretation

* Single failed logon events are commonly caused by user error and do not warrant alerts
* Repeated failed logons in a short timeframe indicate potential brute-force activity
* Context, frequency, and event sequence are critical for severity determination

---

## 🚨 SOC Recommendation

* Implement alerting thresholds for repeated failed logon attempts
* Monitor accounts with multiple authentication failures followed by success
* Correlate authentication events with source system and time window before escalation

---

## ✅ Outcome

Successfully simulated and investigated Windows authentication events, demonstrating endpoint-focused SOC investigation and log analysis skills.

---

*Author: Sriraam*
