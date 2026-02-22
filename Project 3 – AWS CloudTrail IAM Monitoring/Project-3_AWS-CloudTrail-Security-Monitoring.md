# ☁️ AWS CloudTrail Security Monitoring (Cloud SOC Lab)

## 📌 Project Title

**AWS CloudTrail Security Monitoring and IAM Activity Analysis**

---

## 🎯 Objective

To understand **cloud security monitoring** from a SOC analyst perspective by enabling **AWS CloudTrail**, generating **IAM activity**, and analyzing **cloud audit logs** to identify authorized, unauthorized, and service-based actions.

---

## 🛠️ Tools & Technologies Used

* AWS CloudTrail
* AWS IAM
* AWS S3
* AWS STS (Security Token Service)
* AWS Management Console

---

## 🧪 Environment Setup

* Created an AWS account
* Enabled AWS CloudTrail with the following settings:

  * Management events enabled
  * Multi-region trail enabled
  * Logs stored in Amazon S3
* Data events and Insights **not enabled** to avoid unnecessary costs

---

## 🔁 Methodology / Steps Performed

### 1️⃣ CloudTrail Configuration

* Created a CloudTrail named **SOC-Trail**
* Enabled logging for **management events**
* Verified CloudTrail activity using **Event History**

---

### 2️⃣ Initial Log Analysis

Reviewed default CloudTrail events generated during setup, including:

* `CreateTrail`
* `StartLogging`
* `CreateBucket`

✔️ Identified these as **setup-related management events**

---

### 3️⃣ Understanding Service-Based Activity

* Observed multiple `AssumeRole` events
* Identified these as **AWS service-initiated actions**
* Learned how AWS services authenticate using **STS and service roles**
* Distinguished between:

  * Human user activity
  * AWS internal service activity

---

### 4️⃣ IAM User Simulation (Advanced Step)

* Created a low-privileged IAM user (**test-user**)
* Logged in using the IAM sign-in URL
* Attempted to access restricted services such as:

  * Amazon S3
* Encountered `AccessDenied` / failed authorization errors

---

### 5️⃣ Security Event Detection

* Returned to **CloudTrail Event History**
* Filtered logs using:

  * User name
  * Event source
  * Error code
* Identified unauthorized access attempts
* Analyzed the following fields:

  * User identity
  * Event source
  * Error code
  * Event time

---

## 👀 Observations

* CloudTrail logs **both successful and failed** actions
* Unauthorized attempts appear as `AccessDenied` or `UnauthorizedOperation`
* AWS services generate significant background activity using service roles
* Not all authentication-related events appear instantly due to logging delay
* UI access does **not** equal permission to perform API-level actions

---

## 🧠 SOC Analysis & Interpretation

* Single `AccessDenied` events from low-privileged users are generally expected
* Repeated unauthorized attempts may indicate:

  * Misconfiguration
  * Privilege misuse
  * Potential malicious behavior
* Service role `AssumeRole` events are normal and should not trigger alerts unless abnormal

---

## 📚 Key Learnings

* How cloud audit logging works using AWS CloudTrail
* Difference between **authentication vs authorization** in AWS
* Understanding IAM roles, STS, and service principals
* How SOC analysts separate normal cloud noise from threats
* Importance of log-based investigation over UI behavior

---

## ✅ Outcome

Successfully simulated and analyzed real AWS security events using **CloudTrail**, demonstrating the ability to:

* Monitor cloud account activity
* Identify unauthorized actions
* Interpret cloud audit logs from a SOC analyst perspective

---

## 🏢 Use Case in a Real SOC

This project reflects how SOC analysts:

* Investigate IAM misuse
* Monitor cloud account activity
* Validate whether events are benign or suspicious
* Respond to unauthorized access attempts

---

*Author: Sriraam*
