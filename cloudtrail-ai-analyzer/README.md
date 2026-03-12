# AI-Powered CloudTrail Anomaly Detector

## Overview
A local AI-powered security tool that analyzes AWS CloudTrail logs and performs 
automated SOC-style threat detection using a locally running LLM (Qwen 2.5 via Ollama).

## What It Does
- Parses AWS CloudTrail JSON logs
- Sends each event to a local LLM for SOC-style analysis
- Returns severity rating, suspicion assessment, MITRE ATT&CK mapping, and recommended action
- Generates a structured incident report

## Tools & Technologies
- Python
- Ollama (local LLM runtime)
- Qwen 2.5 Coder 7B (local AI model)
- AWS CloudTrail log format

## Project Structure
```
cloudtrail-ai-analyzer/
├── logs/
│   └── cloudtrail.json       # CloudTrail log input
├── analyzer.py               # Main analysis script
├── report.txt                # Auto-generated incident report
└── README.md
```

## Sample Output
Each event is analyzed and returns:
- **SEVERITY**: LOW / MEDIUM / HIGH / CRITICAL
- **SUMMARY**: What happened in plain English
- **SUSPICION**: Why it may or may not be suspicious
- **MITRE_TECHNIQUE**: Mapped ATT&CK technique
- **RECOMMENDED_ACTION**: SOC analyst next steps

## How To Run
1. Install Ollama and pull Qwen model:
```bash
ollama pull qwen2.5-coder:7b
```
2. Place your CloudTrail JSON log in `logs/cloudtrail.json`
3. Run the analyzer:
```bash
python analyzer.py
```
4. Review output in terminal and `report.txt`

## Skills Demonstrated
- Cloud security log analysis (AWS CloudTrail)
- AI/LLM integration for security automation
- SOC alert triage and incident reporting
- MITRE ATT&CK framework mapping
- Python scripting for security tooling
