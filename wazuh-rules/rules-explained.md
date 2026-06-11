# Wazuh Custom Rules — Documentation

## Rule 100092 — VirusTotal File Found
- **Trigger:** VirusTotal returns information about a file
- **Level:** 12 (High)
- **Purpose:** Confirms file was checked against VirusTotal

## Rule 100093 — VirusTotal Malicious File Detected
- **Trigger:** Rule 100092 fired AND virustotal.malicious = 1
- **Level:** 14 (Critical)
- **Purpose:** Triggers active response to delete malicious file
- **MITRE:** T1204 — User Execution
- **Action:** remove-threat.sh deletes the file automatically

## Rule Chain Logic
VirusTotal responds → 100092 fires → if malicious → 
100093 fires → active response deletes file
