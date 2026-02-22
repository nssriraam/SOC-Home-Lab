# Wazuh SIEM Deployment & Troubleshooting

## Overview
This project documents the deployment, configuration, and troubleshooting of a Wazuh SIEM environment. The focus is on resolving real-world issues encountered during installation and integration of Wazuh Manager, Wazuh Indexer (OpenSearch), and the Wazuh Dashboard.

Unlike a standard setup guide, this project emphasizes debugging failures, analyzing logs, and restoring service availability—skills critical for SOC and security engineering roles.

## Objectives
- Deploy a Wazuh SIEM stack in a Linux environment
- Troubleshoot service startup failures and connectivity issues
- Diagnose API, indexer, and dashboard communication problems
- Understand Wazuh internal components and dependencies
- Gain real-world SIEM troubleshooting experience

## Tools and Environment
- Wazuh Manager
- Wazuh Indexer (OpenSearch)
- Wazuh Dashboard
- Linux (Ubuntu)
- systemd services
- Journal logs and application logs

## Issues Encountered
The following issues were encountered during deployment:
- Wazuh Dashboard showing "Server not ready yet"
- Wazuh API connection failures (ECONNREFUSED on port 55000)
- Wazuh Indexer failing to start due to disk space exhaustion
- Authentication and authorization errors between services
- Incomplete or corrupted registry and cache files
- Service dependency and startup order issues

## Troubleshooting Performed
The troubleshooting process included:
- Analyzing system logs using `journalctl`
- Verifying service status with `systemctl`
- Inspecting open ports and listening services
- Clearing corrupted dashboard cache and registry files
- Reinstalling and reconfiguring Wazuh components
- Expanding disk space to resolve indexer failures
- Validating API availability and authentication
- Restarting services in the correct dependency order

## Root Cause Analysis
The primary root causes identified were:
- Insufficient disk space causing Wazuh Indexer startup failures
- Incomplete service initialization leading to API unavailability
- Dashboard cache corruption after failed startups
- Misalignment between running services and expected ports

## Outcome
Although the deployment encountered multiple failures, the troubleshooting process provided deep insight into Wazuh architecture and real-world SIEM operations. This project demonstrates the ability to diagnose, analyze, and remediate complex issues in a production-like environment.

## Key Skills Gained
- SIEM troubleshooting and debugging
- Wazuh architecture understanding
- Linux service and log analysis
- Root cause analysis
- Incident-style problem solving
- Persistence and systematic investigation
