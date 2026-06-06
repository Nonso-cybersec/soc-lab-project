# Ethical Hacking Class 1 — Foundation & Methodology

## Date
June 5, 2026

## What is Ethical Hacking
Testing of web, web apps, software or APIs in a 
virtual environment with written authorization from 
the organization. A signed document defines the scope 
and separates an ethical hacker from a malicious one.
Goal is to help the business thrive, not harm it.

## PTES — 7 Phases

1. **Pre-Engagement** — Most important phase. Defines 
   scope, rules of engagement, and authorization.

2. **Intelligence Gathering** — OSINT and reconnaissance. 
   Collecting information about the target.

3. **Threat Modelling** — Identifying org assets and how 
   an attacker would exploit them.

4. **Vulnerability Analysis** — Scanning for vulnerabilities 
   using assets identified in threat modelling.

5. **Exploitation** — Exploiting found vulnerabilities 
   to gain access.

6. **Post Exploitation** — Maintaining persistence, 
   lateral movement, data exfiltration, covering tracks.

7. **Reporting** — Documenting findings, evidence, 
   and remediation recommendations.

## Frameworks Covered
- **OWASP** — Focuses on web application security
- **WSTG** (Web Security Testing Guide) — The 
  pentesting Bible for web applications

## Key Lesson
Authorization + Scope = Ethical Hacker
No Authorization = Criminal

## SOC Analyst Perspective
Every phase of PTES has detection opportunities:
- Intelligence Gathering → detected via honeypots, 
  unusual DNS queries
- Exploitation → detected via IDS/Suricata alerts
- Post Exploitation → detected via Wazuh log analysis,
  unusual process creation, lateral movement alerts
