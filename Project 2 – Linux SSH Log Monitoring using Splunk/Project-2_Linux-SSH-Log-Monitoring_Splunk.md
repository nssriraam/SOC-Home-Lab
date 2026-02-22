# Linux SSH Log Monitoring using Splunk (SOC Home Lab)

## 📌 Project Objective

The objective of this project is to simulate a real-world **SOC analyst workflow** by collecting, ingesting, and analyzing **Linux SSH authentication logs** in **Splunk Enterprise**. The lab focuses on detecting suspicious SSH activities such as **failed login attempts**, **invalid users**, and **potential brute-force attacks**.

---

## 🧪 Lab Environment

| Component        | Details                       |
| ---------------- | ----------------------------- |
| Operating System | Kali Linux                    |
| SIEM Tool        | Splunk Enterprise 10.x        |
| Log Source       | systemd journal (SSH service) |
| Log Type         | SSH authentication logs       |
| Index            | `main`                        |
| Source Type      | `linux_secure`                |

---

## 🛠️ Tools & Technologies Used

* Splunk Enterprise (SIEM)
* Linux (Kali)
* systemd / journald
* SSH
* SPL (Search Processing Language)

---

## 🔁 Project Workflow

### 1️⃣ Splunk Installation & Setup

* Installed **Splunk Enterprise** on Kali Linux
* Started Splunk service
* Accessed Splunk Web UI via `http://localhost:8000`
* Logged in using administrator credentials

---

### 2️⃣ Log Collection (Key Learning)

* Kali Linux **does not use** `/var/log/auth.log`
* SSH logs are stored in the **systemd journal**
* Extracted SSH logs manually into a readable file

```bash
sudo journalctl -u ssh --since "today" > /tmp/ssh_journal.log
```

✔️ This step highlights an important SOC skill: adapting log collection methods based on OS differences.

---

### 3️⃣ Log Ingestion into Splunk

* Navigated to **Add Data → Monitor**
* Monitored the following file:

```
/tmp/ssh_journal.log
```

* Configured Splunk input settings:

  * **Source Type:** `linux_secure`
  * **Index:** `main`
  * **Host:** Kali

✔️ Logs were successfully parsed and indexed.

---

### 4️⃣ Attack Simulation

To generate suspicious SSH events:

```bash
ssh fakeuser@localhost
```

This produced:

* Failed password attempts
* Invalid user authentication attempts
* Pre-authentication connection drops

✔️ Simulates a real-world **SSH brute-force attack scenario**.

---

### 5️⃣ Log Analysis in Splunk

* Performed log analysis using **SPL queries**
* Verified real-time ingestion and timestamps
* Analyzed authentication patterns and event timelines

---

## 🔍 Sample SPL Queries

```spl
index=main sourcetype=linux_secure
```

```spl
index=main ("Failed password" OR "Invalid user")
```

```spl
index=main source="/tmp/ssh_journal.log"
```

```spl
index=main "sshd" | stats count by user
```

---

## 📊 Findings & Results

* Successfully detected:

  * Multiple failed SSH login attempts
  * Invalid user authentication attempts
  * Repeated SSH connections
* Demonstrated how **SSH brute-force attacks** appear in SIEM logs
* Confirmed proper log parsing and indexing in Splunk
* These events align with **Initial Access (Credential Access)** detection use cases monitored by SOC teams

---

## ✅ Key Takeaways

* Understanding OS-specific logging mechanisms is critical for SOC analysts
* Splunk can effectively detect SSH-based brute-force attacks
* SSH authentication logs are a valuable data source for **early attack detection**
* This lab mirrors real SOC monitoring and investigation workflows

---

## 📁 Project Type

**SOC Home Lab / Blue Team / SIEM Monitoring**

---

*Author: Sriraam*
