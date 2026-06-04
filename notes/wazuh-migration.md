## Wazuh Architecture Migration — June 2026

### Decision
Moved Wazuh Manager from Kali to Ubuntu.

### Reason
- Kali is an attack machine — SIEM should not run on it
- Attack traffic from Kali was polluting SIEM logs
- Correct architecture: Ubuntu = defender, Kali = attacker

### Architecture After Migration
- Ubuntu 192.168.10.20 → Wazuh Manager + Dashboard
- Kali 192.168.10.10 → Wazuh Agent + Attack machine
- Windows Server 192.168.10.30 → Wazuh Agent + Domain Controller

### Lesson Learned
Never build on wrong architecture — fix it early before
everything depends on it.
