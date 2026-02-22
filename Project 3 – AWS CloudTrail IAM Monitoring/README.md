# Project 3 – AWS CloudTrail IAM Security Monitoring

## Overview
This project focuses on monitoring AWS IAM activity using AWS CloudTrail logs to detect unauthorized access, privilege escalation, and suspicious API activity. The goal is to simulate a Cloud SOC environment and analyze identity-related security events in AWS.

## Objectives
- Monitor AWS IAM activity using CloudTrail logs
- Detect suspicious API calls and unauthorized access attempts
- Identify privilege escalation and policy modification events
- Understand cloud-based SOC monitoring workflows

## Tools and Environment
- AWS CloudTrail
- AWS IAM
- AWS Management Console
- CloudTrail event logs

## Data Collection
CloudTrail was configured to capture management events related to IAM activity. The collected logs include:
- IAM user and role activity
- Policy creation, deletion, and modification
- Access key usage and changes
- Login and authentication-related events

## Analysis Performed
The following analysis was performed on CloudTrail logs:
- Detection of `ConsoleLogin` events and failed login attempts
- Monitoring of IAM policy changes such as `AttachUserPolicy` and `PutUserPolicy`
- Identification of access key creation and deletion
- Review of high-risk API calls indicating potential privilege escalation

## Findings
- IAM policy changes were successfully detected through CloudTrail logs
- Unauthorized or unexpected IAM actions can be quickly identified
- Monitoring identity-related events is critical for preventing account compromise

## Outcome
This project demonstrates practical cloud security monitoring skills and highlights how CloudTrail plays a key role in AWS SOC operations for detecting identity-based threats.

## Key Skills Gained
- AWS CloudTrail log analysis
- IAM security monitoring
- Cloud SOC investigation techniques
- Privilege escalation detection
- AWS security event analysis
