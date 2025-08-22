
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

<img width="1006" height="855" alt="sada" src="https://github.com/user-attachments/assets/e7815e09-394d-40bf-96dc-c01221c7b678" /><br>


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

<img width="714" height="476" alt="sysmonnn" src="https://github.com/user-attachments/assets/420ed5fd-9eab-45c5-b9fa-f47a3516fdd8" /><br>


#### 4.Setting Up SplunkSince we have installed Splunk on the Ubuntu Server, we assign an IP address to our Splunk machine

##### - Since we have installed Splunk on the Ubuntu Server, we assign an IP address to our Splunk machine.

<img width="930" height="319" alt="ip lin" src="https://github.com/user-attachments/assets/ab527ea0-14cd-4e37-af3a-3b10e345c8e6" /> <br>

##### - Creating a Splunk Indexer

<img width="1193" height="479" alt="indexer" src="https://github.com/user-attachments/assets/db22e811-368d-4760-86a1-a29b6a391bb1" /><br>

##### - Installing Splunk-Forward on windows 10 machine. 

- **Enable port 9997** -> settings -> Forwarding and receiving -> Configure Receiving. (for receiving data)

  <img width="1021" height="359" alt="9997" src="https://github.com/user-attachments/assets/d703e916-f415-48f1-a718-b65f41f54bdb" />

- We need some configuration in **inputs.conf**

<img width="1140" height="780" alt="splunkfwrd" src="https://github.com/user-attachments/assets/0409ce59-8e82-4a5a-aff7-4b1bb50b7719" /><br>

- By default, the Splunk Forwarder account cannot read Sysmon logs, so we go to Splunk services and enable the **Local System account** to push all logs to the Splunk Forwarder.

<img width="8017" height="625" alt="services" src="https://github.com/user-attachments/assets/23518ff1-96bf-4a01-89a5-7e003097f80d" /><br>

- **Splunk has been successfully configured**

<img width="833" height="658" alt="splunksoosss" src="https://github.com/user-attachments/assets/25961d90-640c-4afb-b1a9-2f89cb1b2874" /><br>


#### 5.Configure Zeek & Suricata
-First, assign a static IP address.

<img width="902" height="266" alt="Screenshot 2025-08-22 234948" src="https://github.com/user-attachments/assets/7ac4f33d-6605-4ea2-9570-417e3046091b" /><br

-Forward **Zeek and suricata logs** to my Splunk server

<img width="805" height="509" alt="Screenshot 2025-08-23 000045" src="https://github.com/user-attachments/assets/e1830d5d-0b59-408b-a06c-9044c35674db" /><br>

-**Zeek and Suricata logs have been successfully configured**

<img width="1018" height="762" alt="zeek logs" src="https://github.com/user-attachments/assets/f8588571-4b4d-43b9-952a-4bbbf22b5bb6" /><br>
*This setup proved to be particularly challenging. Not all of the steps have been documented here to avoid making this section excessively long.

#### 6.Configure PFSense Firewall

##### -Configure pfSense: I want to send Syslog to my Splunk server, but before that, I need to install the proxy log.<br> 

<img width="1105" height="882" alt="pfsense" src="https://github.com/user-attachments/assets/fff31e74-9df6-4734-a35c-3caf5abdbfc0" /><br>

- Install Proxy log - **SquidProxy** <br> 
System -> Package Management -> Available Packages -> Search for Squid
<img width="940" height="646" alt="7 3" src="https://github.com/user-attachments/assets/404bf223-fbb9-41e6-a7c2-e8cff5296f08" />

-Installing Splunk Forwarder

<img width="952" height="896" alt="pfsense splunkfowraed7 4" src="https://github.com/user-attachments/assets/1780d704-14dd-4b9e-accb-e0b8aa469f89" /><br>

-Creating file **input.conf**

<img width="913" height="643" alt="inputs" src="https://github.com/user-attachments/assets/023d3816-7dac-49d5-9ca3-08d0c6165f44" /><br>

-Firewall logs have been successfully parsed.<br>

<img width="1022" height="722" alt="pfsese" src="https://github.com/user-attachments/assets/cd073f13-08de-42d9-8392-abadd502ba79" />


#### 7.Generating Telemetry

#### 8



