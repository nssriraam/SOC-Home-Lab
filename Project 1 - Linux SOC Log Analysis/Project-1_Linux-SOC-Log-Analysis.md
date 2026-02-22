# 🧩 SOC Log Analysis (Linux / Kali)

## 🎯 Objective

Analyze Linux authentication logs to identify **suspicious SSH login attempts**, simulating a basic **SOC analyst investigation** workflow.

---

## 🛠️ Tools Used

* Kali Linux
* `journalctl`
* SSH

---

## 🔍 What I Did

* Simulated failed SSH login attempts using an **invalid user account**
* Generated authentication failure events on the system
* Analyzed SSH authentication logs using **journalctl**
* Filtered logs by:

  * SSH service
  * Time range
  * Failure-related keywords
* Reviewed log patterns to identify suspicious behavior

---

## 📊 Findings

* Observed **multiple failed SSH login attempts** for an invalid (non-existent) user
* Attempts originated from the **same source IP** within a short time window
* Activity pattern indicates **potential brute-force behavior**
* This behavior resembles common **initial access attempts** seen in real-world attacks

---

## 🚨 Event Summary

| Field      | Details                                     |
| ---------- | ------------------------------------------- |
| Event Type | Authentication failure                      |
| Service    | SSH                                         |
| User       | Invalid / non-existent                      |
| Pattern    | Repeated failed attempts                    |
| Risk       | Potential brute-force attempt               |
| Severity   | Low (lab / localhost), Medium in production |

---

## 🛡️ SOC Action Recommendation

In a real production environment:

* This activity should **trigger a SOC alert**
* Source IP should be **monitored or temporarily blocked**
* Implement authentication hardening measures such as:

  * Rate limiting
  * `fail2ban`
  * Strong authentication policies

---

## ✅ Key Takeaways

* Authentication logs are critical for **early attack detection**
* Repeated failed logins are a strong indicator of **brute-force attempts**
* Even low-severity lab events map directly to **real SOC use cases**

---

*Author: Sriraam*
