# Cybersecurity-Labs-Projects
Hands on cybersecurity projects focused on blue team/soc analyst skills
# About Me
Transitioning from dental technology to cybersecurity with a focus on defensive security and SOC analysis. This repository documents my hands on learning journey.

## Project 1: Security Monitoring Home Lab

**Date:23 January 2026

### Overview
Built an isolated virtual network environment to practice security monitoring, traffic analysis, and defensive security techniques.

### Objectives
- Set up a functional home lab for practicing SOC analyst skills
- Create an isolated network for safe security testing
- Establish baseline for future security monitoring projects

### Tools & Technologies
- **Virtualization:** Oracle VirtualBox 7.2.4
- **Attack/Analysis Platform:** Kali Linux 2025.4
- **Target System:** Windows 11
- **Network Configuration:** Host-only networking (192.168.56.0/24)

### Implementation Steps

1. **Environment Setup**
   - Installed Oracle VirtualBox on host machine (16GB RAM)
   - Downloaded and extracted Kali Linux VirtualBox image
   - Downloaded Windows 11 ISO and created new VM

2. **Network Configuration**
   - Configured both VMs with Host-only Adapter
   - Verified isolated network connectivity
   - Assigned IP addresses:
     - Kali Linux: 192.168.56.101
     - Windows 11: 192.168.56.102

3. **Connectivity Testing**
   - Performed bidirectional ping tests between VMs
   - Verified network isolation from host network

### Challenge Encountered

**Problem:** Initial ping tests from Kali to Windows showed 100% packet loss (401 packets transmitted, 0 received), while Windows to Kali worked fine.

**Root Cause:** Windows Firewall was blocking ICMP Echo Requests by default.

**Solution:** Enabled the "File and Printer Sharing (Echo Request - ICMPv4-In)" inbound rule in Windows Defender Firewall with Advanced Security, restoring full bidirectional connectivity.

**Lesson Learned:** Even in isolated lab environments, default security configurations can impact testing. Understanding firewall rules and their impact on network protocols is crucial for SOC work.

### Results
- Successfully established isolated virtual network
- Verified bidirectional communication between systems
- Created foundation for future security monitoring exercises

### Next Steps
- Install and configure Wireshark for traffic analysis
- Set up Windows event logging
- Simulate basic attacks and analyze network traffic
- Deploy SIEM solution (Wazuh or Security Onion)

---

## Skills Demonstrated
- Virtual machine configuration and management
- Network troubleshooting
- Windows Firewall configuration
- Basic network connectivity testing
- Technical documentation

## Certifications & Training
- Google Cybersecurity Certificate (Completed)
- Cisco Junior Security Analyst Path (In Progress)
- CompTIA Security+ (In Progress)
- TryHackMe Pre-Security Path (In Progress)
