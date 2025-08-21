
# Detection Lab

## Objective

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Splunk - Security Information and Event Management (SIEM) system for log ingestion and analysis.
- pfSense Firewall – Firewall and traffic management system that forwards logs to Splunk for analysis.
- Zeek & Suricata - Network security tools for traffic analysis and intrusion detection, forwarding logs and alerts to Splunk for analysis.
- Active Directory - Domain controller managing user accounts, authentication, and configuring audit policies, while sending security logs to Splunk.
- Kali Linux & Atomic Red Team - Telemetry generation tools to create realistic network traffic and attack scenarios.
---

## Steps Taken

#### 1.Creating the network diagram.

-At the beginning, I drew a network diagram in draw.io to logically outline my plan. Imagine this as a small business environment, implemented across six separate virtual machines.

<img width="607" height="640" alt="draw iooo" src="https://github.com/user-attachments/assets/20c08eb5-664f-4435-80ae-82f7184fa4e3" />


#### 2.Installing pfSense Firewall.

-Configure two network adapters and assign IPs: one for WAN and one for LAN.<br>
 *Note*: WAN should have internet access, LAN stays internal.
 
<img width="850" height="539" alt="pfsense" src="https://github.com/user-attachments/assets/cc641932-509e-432a-9f1d-dc8f5b7f5553" />
<img width="750" height="722" alt="pfsense" src="https://github.com/user-attachments/assets/646903d4-deac-4332-ac35-ed2a96dae715" />







