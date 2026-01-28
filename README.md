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

### Screenshots
![WhatsApp Image 2026-01-23 at 5 46 04 AM](https://github.com/user-attachments/assets/f9d2bc1d-8526-4133-b5c2-771298baf396)
![WhatsApp Image 2026-01-23 at 5 46 05 AM (1)](https://github.com/user-attachments/assets/087bfa67-eb93-4bb4-9c44-65f49be4e442)
![WhatsApp Image 2026-01-23 at 5 46 05 AM](https://github.com/user-attachments/assets/ce9754ea-fc84-4783-837b-b7a1211f9da2)
![WhatsApp Image 2026-01-23 at 5 46 06 AM](https://github.com/user-attachments/assets/23614048-1921-4b4a-a21e-1459ccff7bd7)


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







## Project 2: Windows Event Log Analysis

*Date:* January 2026

### Overview
Learned to navigate and analyze Windows Security Event Logs to identify user activities, administrative actions, and potential security incidents. This is a foundational skill for SOC analysts who spend significant time reviewing logs for suspicious behavior.

### Objectives
- Understand Windows Event Viewer structure and navigation
- Learn critical Event IDs for security monitoring
- Practice filtering and analyzing security events
- Identify normal vs. suspicious activity patterns

### Tools & Technologies
- Windows 11 Event Viewer
- Security Event Logs
- Event filtering and analysis

### Key Event IDs Learned

*Authentication & Access:*
- *4624* - Successful account logon
  - Logon Type 2: Interactive (physical login)
  - Logon Type 3: Network access
  - Logon Type 5: Service account
  - Logon Type 10: Remote Desktop
- *4625* - Failed logon attempt (important for detecting brute force attacks)
- *4648* - Logon attempted with explicit credentials

*Account Management:*
- *4672* - Special privileges assigned to new logon (admin rights)
- *4726* - User account was deleted

*System Events:*
- *1102* - Security audit log was cleared (potential evidence tampering)

### Hands-On Activities

1. *Navigated Windows Security Logs*
   - Opened Event Viewer (eventvwr.msc)
   - Located Security logs under Windows Logs
   - Analyzed 4,225+ security events from fresh Windows 11 installation

2. *Filtered Specific Event Types*
   - Filtered for Event ID 4624 (successful logons): 547 events
   - Filtered for Event ID 4672 (privileged access): 524 events
   - Filtered for Event ID 4648 (explicit credentials): 26 events
   - Distinguished between system accounts (SYSTEM, COMPUTER$) and actual user activity

3. *Generated and Analyzed Security Events*
   - Created new administrative user account
   - Deleted old user account (Event ID 4726)
   - Performed administrative password reset
   - Observed corresponding security events in real-time

### Challenge Encountered

*Problem:* Lost access to primary user account due to forgotten password during testing.

*Solution:* Accessed Windows Recovery Environment, used Command Prompt to activate built-in Administrator account (net user administrator /active:yes), gained system access, created new admin user, and deleted compromised account. All actions generated audit trail in Security logs.

*Lesson Learned:* Even troubleshooting and recovery actions create security events. In a real SOC environment, these activities would need to be properly documented and justified. Also highlighted the importance of secure password management and the value of having multiple admin accounts for recovery scenarios.

### Key Observations

*Normal vs. Suspicious Patterns:*
- Most security events (80%+) are automated system processes (services, scheduled tasks)
- Real user activity represents a smaller subset requiring focused analysis
- Event ID context matters: Same Event ID can indicate normal or suspicious activity depending on:
  - Time of occurrence
  - Account involved
  - Frequency/patterns
  - Associated events

*Important for SOC Work:*
- Filtering is essential - raw logs contain too much noise
- Must understand difference between system accounts and user accounts
- Event ID 1102 (log cleared) is a major red flag for incident response
- Account creation/deletion events should always be investigated
- Failed login attempts (4625) + successful login (4624) pattern often indicates credential attacks

### Screenshots

*Audit Log Cleared Event:*

![Audit log cleared - Event ID 1102](![WhatsApp Image 2026-01-28 at 4 25 23 PM (1)](https://github.com/user-attachments/assets/91d09542-1ffd-4425-9aeb-26ef244a14e2)


This event (1102) is generated when someone clears the Security log - a common technique attackers use to cover their tracks.

### Skills Demonstrated
- Windows Event Viewer navigation and analysis
- Security log filtering and investigation
- Event ID identification and interpretation
- Distinguishing normal system activity from user actions
- Understanding logon types and their security implications
- Windows account management and recovery
- Technical troubleshooting under constraints

### Real-World Application
These skills directly translate to SOC analyst responsibilities:
- Investigating suspicious login attempts
- Detecting privilege escalation
- Identifying unauthorized account changes
- Recognizing evidence tampering (log clearing)
- Correlating multiple events to build incident timeline
