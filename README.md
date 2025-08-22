
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



#### 3.Setting Up Active Directory

##### -First, assign a static IP address.

<img width="1006" height="855" alt="sada" src="https://github.com/user-attachments/assets/e7815e09-394d-40bf-96dc-c01221c7b678" />


##### -After assigning a static IP address, install Active Directory.

<img width="1021" height="878" alt="install acd" src="https://github.com/user-attachments/assets/e66b4487-73d0-4702-a76f-c970f1618255" /><br>

##### -I created three departments with one user each, as commonly done in many Active Directory environments.

<img width="1026" height="875" alt="create a user" src="https://github.com/user-attachments/assets/1420c265-d5a0-4583-b13c-bc3d7e82bc3f" />

##### -Configured the Windows 10 client to join the Active Directory domain using the created user account.Below is a screenshot showing how to log in with the created user account.

<img width="800" height="500" alt="create a win10" src="https://github.com/user-attachments/assets/1ab0d41e-1b0f-4c71-93dd-fadc232f8437" />

##### -Configuring Logging Policies  - Group Policy Object
- Create a GPO and name it "Group Policy – Endpoint"
<img width="1032" height="876" alt="gpoo" src="https://github.com/user-attachments/assets/dafc44fa-67e1-4aef-adac-7c8143197e2e" />

 
- Configure my environment according to Microsoft’s baseline recommendations.

<img width="1021" height="683" alt="gpo2" src="https://github.com/user-attachments/assets/880e892f-e81e-4ec5-8e82-4f1af1f31ee5" /><br>


- Reviewing a Microsoft security baseline recommendation and let's see in the screenshot above how we successfully completed it.()
  
<img width="712" height="292" alt="sgo3" src="https://github.com/user-attachments/assets/f2487ac8-62f7-4343-8fdf-843f56764bf1" /><br>

- Enable monitoring for brute force activity and administrative privileges

<img width="798" height="614" alt="gpo5" src="https://github.com/user-attachments/assets/94098945-6f21-46dd-9e8b-e656b2bf0a8d" /><br>

- Enable Process tracking EventID - 4688 (not enabled by default)

<img width="800" height="5000" alt="4688" src="https://github.com/user-attachments/assets/944cd73d-c98d-4a76-b319-27319fb789bb" /><br>

- Installed Sysmon to enhance telemetry collection

<img width="714" height="476" alt="sysmonnn" src="https://github.com/user-attachments/assets/420ed5fd-9eab-45c5-b9fa-f47a3516fdd8" />



#### 4

#### 5

#### 6

#### 7

#### 8



