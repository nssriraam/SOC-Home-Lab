# Project 2 – Linux SSH Log Monitoring using Splunk

## Overview
This project focuses on monitoring and analyzing Linux SSH authentication logs using Splunk. The objective is to detect suspicious login activity such as brute-force attempts, failed logins, and unauthorized access by visualizing and querying SSH log data.

## Objectives
- Centralize Linux SSH logs in Splunk
- Detect failed and successful SSH login attempts
- Identify brute-force attack patterns
- Build searches and alerts for suspicious SSH activity
- Understand real-world SOC monitoring workflows

## Tools and Environment
- Linux (Ubuntu)
- SSH service
- Splunk Enterprise
- Linux authentication logs (`/var/log/auth.log`)

## Data Collection
SSH authentication logs were collected from the Linux system and forwarded to Splunk using a log forwarder. The logs include:
- Failed SSH login attempts
- Successful SSH logins
- Source IP addresses
- Usernames and timestamps

## Analysis Performed
The following analysis was performed using Splunk Search Processing Language (SPL):
- Count of failed SSH login attempts by source IP
- Detection of repeated failed logins within short time intervals
- Identification of successful logins following multiple failures
- Visualization of login trends over time

## Findings
- Multiple failed SSH login attempts from the same IP were detected, indicating possible brute-force attacks
- Successful logins following repeated failures highlighted potential compromised credentials
- Time-based patterns helped identify peak attack periods

## Outcome
This project demonstrates practical SOC skills in log monitoring, threat detection, and investigation using Splunk. It reflects real-world scenarios handled by SOC analysts to identify and respond to unauthorized access attempts.

## Key Skills Gained
- SSH log analysis
- Splunk SPL querying
- Security event monitoring
- Brute-force attack detection
- SOC investigation workflow
