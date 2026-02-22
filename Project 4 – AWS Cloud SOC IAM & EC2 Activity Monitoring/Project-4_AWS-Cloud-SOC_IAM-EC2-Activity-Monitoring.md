# ☁️ AWS Cloud SOC – IAM & EC2 Activity Monitoring using CloudTrail

## 🎯 Objective

To simulate **real-world SOC monitoring** in an AWS cloud environment by tracking **IAM user activity**, **EC2 provisioning actions**, and **security group misconfigurations** using **AWS CloudTrail**, followed by remediation and verification.

---

## 🛠️ Tools & Technologies Used

* Amazon Web Services (AWS)
* AWS CloudTrail
* IAM (Identity and Access Management)
* EC2 (Elastic Compute Cloud)
* Security Groups
* AWS Management Console

---

## 🔍 Project Scope

* Monitor actions performed by an **IAM user** instead of the root account
* Detect **privileged cloud activities**
* Identify **insecure network configurations**
* Perform remediation and **verify changes through CloudTrail logs**

---

## 🧪 Environment Setup

### 1️⃣ IAM User Configuration

* Created IAM user: **cloud-soc-test-user**
* Enabled AWS Management Console access
* Attached policy: **AdministratorAccess**
* Used IAM user for all cloud actions (root account avoided)

---

### 2️⃣ CloudTrail Verification

* Confirmed **CloudTrail Event History** enabled by default
* Used root account only to **review and investigate logs**
* Focused analysis on:

  * Event name
  * Username
  * Source IP
  * Resource affected

---

## 🔁 Activities Performed & Analysis

### 1️⃣ EC2 Instance Launch

**Action:**

* IAM user launched an EC2 instance using **Amazon Linux 2023 AMI**
* Instance type: `t3.micro` (Free Tier)

**CloudTrail Event Identified:**

* `RunInstances`
* Event source: `ec2.amazonaws.com`
* User: `cloud-soc-test-user`
* Source IP: Public IP address recorded

**SOC Relevance:**

* Detects unauthorized or unexpected instance provisioning
* Important for **cost abuse** and **persistence detection**

---

### 2️⃣ Key Pair Creation

**Action:**

* Created EC2 key pair for SSH access

**CloudTrail Event:**

* `CreateKeyPair`

**SOC Insight:**

* Key creation may indicate preparation for **persistent access**

---

### 3️⃣ Security Group Creation

**Action:**

* Created custom security group: `cloud-soc-sg`

**CloudTrail Event:**

* `CreateSecurityGroup`

---

### 4️⃣ Insecure Inbound Rule Detected

**Action:**

* Allowed inbound:

  * SSH (22) from `0.0.0.0/0`
  * HTTP (80) from `0.0.0.0/0`

**CloudTrail Event:**

* `AuthorizeSecurityGroupIngress`

**SOC Finding:**

* **Critical misconfiguration**
* SSH exposed to the internet increases brute-force and exploitation risk

---

### 5️⃣ Remediation Performed

**Actions Taken:**

* Removed HTTP (80) rule
* Restricted SSH access to **My IP (/32)**

**CloudTrail Event:**

* `RevokeSecurityGroupIngress`

**Verification:**

* Confirmed updated inbound rules in EC2
* Verified CloudTrail logs reflected remediation activity

---

## 📚 Key SOC Learnings

* IAM usernames are directly traceable in CloudTrail logs
* CloudTrail provides deep visibility into:

  * Privileged actions
  * Network exposure
  * Resource lifecycle changes
* Security misconfigurations can be **detected and validated** using logs
* Remediation actions must always be **verified through audit logs**

---

## ✅ Conclusion

This project demonstrated **real-world Cloud SOC monitoring** by:

* Identifying IAM-driven EC2 activities
* Detecting insecure network configurations
* Validating remediation through CloudTrail logs

The investigation followed a SOC-style workflow:

**Detect → Analyze → Remediate → Verify**

This mirrors practical cloud security operations performed by Cloud SOC teams.

---

*Author: Sriraam*
