<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/lu7knq9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the Domain Controller VM (Windows Server 2022) named “DC-1”

Take note of the Resource Group and Virtual Network (Vnet) that get created at this time

Set Domain Controller’s NIC Private IP address to be static

Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created for domain controller

Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher
</p>
<br />

<p>
<img src="https://i.imgur.com/CC3T4kN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)
  
Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
  
Check back at Client-1 to see the ping succeed

</p>
<br />

<p>
<img src="https://i.imgur.com/hZW78OK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to DC-1 and install Active Directory Domain Services
  
Promote as a DC: Setup a new forest as "mydomain.com" (can be anything, just remember what it is)
  
Restart and then log back into DC-1 as user: mydomain.com\labuser
</p>
<br />
<p>
<img src="https://i.imgur.com/90vVeAD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”
  
Create a new OU named “_ADMINS”
  
Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”
  
Add jane_admin to the “Domain Admins” Security Group
  
Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin”
 

</p>

