# 🛡️ Project: Wazuh SIEM Deployment & Troubleshooting Lab

## 🎯 Objective

Deploy a **self-hosted Wazuh SIEM stack** and analyze deployment failures in a **resource-constrained virtualized environment**, focusing on root cause analysis and SOC-style troubleshooting.

---

## 🧪 Environment

| Component     | Details           |
| ------------- | ----------------- |
| Host OS       | Windows           |
| Hypervisor    | VirtualBox        |
| Guest OS      | Ubuntu Linux      |
| RAM           | 6 GB              |
| Storage       | 40 GB (LVM-based) |
| Wazuh Version | 4.14.x            |

---

## 🧩 Wazuh Stack Components

* Wazuh Manager
* Wazuh Indexer (OpenSearch)
* Wazuh Dashboard

---

## 🔧 Tasks Performed

* Installed **Wazuh all-in-one stack**
* Configured network access and dashboard connectivity
* Verified service availability using:

  * `systemctl`
  * Port inspection tools
* Diagnosed **OpenSearch startup failures** using `journalctl`
* Identified **root filesystem exhaustion** as the primary failure cause
* Expanded **LVM logical volume** to restore disk availability
* Recovered Wazuh API service and validated **port 55000**
* Investigated persistent **dashboard plugin corruption**

---

## 🔍 Key Findings

* OpenSearch fails **silently** when disk space is exhausted
* Partial service initialization can cause **irreversible dashboard plugin corruption**
* Self-hosted SIEM deployments are highly sensitive to:

  * Disk availability
  * JVM stability
  * Resource allocation
* Infrastructure health is **critical** to SIEM reliability

---

## ⚠️ Outcome

* Deployment was **halted intentionally** after confirming environment-level incompatibility
* Findings documented as **real-world SIEM operational risks** rather than configuration errors

---

## 🧠 Skills Demonstrated

* Linux system administration
* LVM disk management
* SIEM architecture understanding
* OpenSearch troubleshooting
* Log-based root cause analysis
* SOC-style failure investigation

---

## ✅ Key Takeaway

This lab demonstrates that **SIEM failures are often infrastructure-driven**, not tool-driven. Effective SOC engineers must be able to identify and remediate **environmental constraints** before attributing issues to security tooling.

---

*Author: Sriraam*
