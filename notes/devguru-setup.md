# DevGuru VulnHub Setup — June 6, 2026

## What is DevGuru
A deliberately vulnerable virtual machine from VulnHub
designed for penetration testing practice. Legal to attack
— built for this purpose.

## Network Configuration
- DevGuru → NAT Network → LabNetwork (10.0.2.0/24)
- Kali → Adapter 1: NAT Network → LabNetwork
- Kali → Adapter 2: Internal Network → soclab

## Key Concepts Learned
- Netdiscover uses ARP to find hosts — can't be blocked
- NAT vs NAT Network difference
- 10.0.2.1 = VirtualBox DHCP/DNS
- 10.0.2.2 = Default gateway to internet
- SATA link down messages = normal on imported VMs

## Next Steps
- Find DevGuru IP using netdiscover
- Run Nmap port scan on DevGuru
- Begin reconnaissance phase
