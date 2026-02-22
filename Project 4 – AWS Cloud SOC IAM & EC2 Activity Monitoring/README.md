# Project 4 – AWS Cloud SOC IAM & EC2 Activity Monitoring

## Overview
This project focuses on monitoring AWS IAM and EC2 activity using AWS CloudTrail logs to detect unauthorized access, misconfigurations, and suspicious behavior in a cloud environment. It simulates real-world Cloud SOC monitoring scenarios involving identity and compute resources.

## Objectives
- Monitor IAM and EC2 activity using AWS CloudTrail
- Detect unauthorized or risky IAM actions
- Identify suspicious EC2 activity such as instance creation, termination, and security group changes
- Understand Cloud SOC workflows for cloud infrastructure monitoring

## Tools and Environment
- AWS CloudTrail
- AWS IAM
- AWS EC2
- AWS Management Console
- CloudTrail management event logs

## Data Collection
CloudTrail was configured to collect management events related to IAM and EC2 services. The logs include:
- IAM user and role activity
- Policy changes and access key operations
- EC2 instance lifecycle events
- Security group and network configuration changes

## Analysis Performed
The following analysis was conducted:
- Monitoring IAM policy creation, attachment, and deletion
- Detection of high-risk IAM actions and privilege escalation attempts
- Tracking EC2 instance creation, termination, and modification events
- Reviewing security group changes that could expose resources publicly
- Correlating IAM and EC2 activity to identify suspicious behavior

## Findings
- IAM misconfigurations and risky permissions can be detected through CloudTrail
- EC2 lifecycle events provide valuable insight into infrastructure changes
- Correlating identity and compute activity improves cloud threat visibility

## Outcome
This project demonstrates hands-on experience with cloud security monitoring and investigation. It highlights how Cloud SOC teams monitor AWS environments to detect threats related to identity abuse and infrastructure changes.

## Key Skills Gained
- AWS CloudTrail analysis
- IAM and EC2 security monitoring
- Cloud SOC investigation techniques
- Cloud infrastructure security
- Detection of misconfigurations and unauthorized activity
