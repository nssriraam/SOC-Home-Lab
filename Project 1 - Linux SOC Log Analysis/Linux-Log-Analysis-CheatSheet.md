# 🧾 Linux SSH Log Analysis – Cheat Sheet

A step-by-step command cheat sheet for **SOC log analysis on Linux (Kali)** using `journalctl` and SSH authentication logs.

---

## 1️⃣ Identify Operating System

Check OS and distribution details:

```bash
cat /etc/os-release
```

---

## 2️⃣ View All System Logs

Display all logs stored in the systemd journal:

```bash
sudo journalctl
```

---

## 3️⃣ View SSH Service Logs Only

Filter logs for the SSH service:

```bash
sudo journalctl -u ssh
```

---

## 4️⃣ View SSH Logs for Today

Limit SSH logs to today’s activity:

```bash
sudo journalctl -u ssh --since today
```

---

## 5️⃣ View Recent SSH Activity (Last 5 Minutes)

Useful during live investigations:

```bash
sudo journalctl -u ssh --since "5 minutes ago"
```

---

## 6️⃣ Filter Failed Login Attempts

Identify failed authentication attempts:

```bash
sudo journalctl -u ssh --since "5 minutes ago" | grep -i failed
```

---

## 7️⃣ Generate Test Failed Logins

Simulate failed SSH authentication events:

```bash
ssh fakeuser@localhost
```

---

## 8️⃣ Exit Log Viewer

Quit the `journalctl` interactive view:

```bash
q
```

---

## ✅ SOC Use Case

These commands help SOC analysts to:

* Quickly identify SSH authentication failures
* Detect brute-force or password-guessing behavior
* Perform fast triage during Linux security investigations

---

*Author: Sriraam*
