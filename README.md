# <h1>Elastic SIEM LAB</h1>
### Description

- In this lab, I detail the process of configuring a home lab environment for Elastic Stack Security Information and Event Management (SIEM) utilizing the Elastic Web portal and a Kali Linux virtual machine (VM). The project includes:
  - Setting Up the Environment: Configuring the Elastic Stack SIEM on the Elastic Web portal and deploying the Kali Linux VM.
  - Agent Installation: Installing and configuring the Elastic agent to collect and forward security data from the Kali VM to the SIEM platform.
  - Generating Security Events: Using tools like Nmap on the Kali VM to create security events.
  - Querying and analyzing the logs within the SIEM to ensure effective monitoring and analysis.
- Through this project, I gained hands-on experience in integrating and managing security data within the Elastic Stack ecosystem.
  
<br />


<h2> Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Kali VM</b>
- <b>Nmap</b>




<h2>Environments Used </h2>

- <b>Elastic Cloud</b>

<h2>Project walk-through:</h2>


### Step 1: Set Up the Accounts

- Created an account using the [Free Trial Elastic Cloud](https://www.elastic.co/cloud) account.
- Set up the Kali Linux VM and added it to VirtualBox.
- [How to set up Kali VM](https://www.youtube.com/watch?v=sAMnXte56yY)

<br />
<br />

### Step 2: Setting Up the Agent to Collect Logs

- Utilized the Elastic Cloud site to add integrations.
- Installed the Elastic Defend agent, which:
  - Protects hosts and cloud workloads with threat prevention and detection.
  - Collects data and sends it to a central system for monitoring.
  - Collected and forwarded logs from the Kali VM to the SIEM.

<p align="center">
<img src="https://i.imgur.com/Pg9EmGl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  

  - Checked status with `sudo systemctl status elastic-agent.service`.
<p align="center">
<img src="https://i.imgur.com/9Cf2gr8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
<br />
<br />
  
### Step 3: Generating Security Events on the Kali VM

- Installed Nmap (Network Mapper) on Kali:
    ```bash
    sudo apt-get install nmap
    ```
<p align="center">
<img src="https://i.imgur.com/hUlE0e7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

  
- Ran several scans:
    ```bash
    sudo nmap <vm-ip>
    sudo nmap -sS <ip address>
    sudo nmap -p- <ip address>
    ```
<p align="center">
<img src="https://i.imgur.com/zAZDyAC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/dVvI49N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
<br />
<br />
  
### Step 4: Querying for Security Events in Elastic SIEM

- In Elastic Development, used Logs under Observability to search and filter:
    - Query: `event.action: "nmap_scan"` or `process.args: "Nmap"`

<p align="center">
<img src="https://i.imgur.com/leRwgvQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
<br />
<br />
  
### Step 5: Creating a Dashboard to Visualize the Events

- Used Elastic Portal to create a new dashboard:
    - Added visualization: `Metrics` -> `Area` -> `Timestamp`
    - Shows the count of events over time.

<p align="center">
<img src="https://i.imgur.com/6E56wHF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
<br />
<br />
  
### Step 6: Creating an Alert

- Used Elastic Portal to set up a new alert rule:
    - Condition: `event.action: "Nmap_scan"`
    - Configured to send an email notification when triggered.
<p align="center">
<img src="https://i.imgur.com/4YoKBGv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
<br />
<br />

[Source](https://medium.com/@aali23/a-simple-elastic-siem-lab-6765159ee2b2)
