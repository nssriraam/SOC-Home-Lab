# 📘 Splunk SSH Monitoring – Cheat Sheet

A quick-reference guide for collecting, simulating, and analyzing **Linux SSH logs** in **Splunk Enterprise** during SOC investigations.

---

## 🗂️ Log Collection

Extract SSH logs from the systemd journal (Kali Linux):

```bash
sudo journalctl -u ssh --since "today" > /tmp/ssh_journal.log
```

---

## 🔍 Verify Log File

Confirm the file exists and contains data:

```bash
ls -l /tmp/ssh_journal.log
```

Preview log entries:

```bash
cat /tmp/ssh_journal.log | head
```

---

## ⚔️ Simulate SSH Attack

Generate failed authentication events:

```bash
ssh fakeuser@localhost
```

This produces:

* Invalid user attempts
* Failed password events
* Pre-authentication failures

---

## 🔎 Splunk Searches (SPL)

Basic SSH log search:

```spl
index=main sourcetype=linux_secure
```

Detect failed and invalid login attempts:

```spl
index=main ("Failed password" OR "Invalid user")
```

Search for invalid users only:

```spl
index=main "invalid user"
```

Search for failed passwords only:

```spl
index=main "failed password"
```

---

## 🛠️ Troubleshooting Tips

If logs do not appear in Splunk:

* ⏱️ Verify **time range** in Splunk search
* 📂 Confirm correct **index** (`main`)
* 🧾 Validate **source / source type**
* 🐧 Kali Linux uses **systemd journald**, not `/var/log/auth.log`
* 🔐 Ensure Splunk has **read permissions** on monitored files

---

## ✅ Usage

This cheat sheet is useful for:

* SOC home labs
* Interview preparation
* Quick troubleshooting during investigations
* SSH brute-force detection practice

---

*Author: Sriraam*
