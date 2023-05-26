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

- Set up resources in Azure and ensure connectivity
- Install Active Directory 
- Join Cilent-1 to domain
- Setup Remote Desktop for nonadminstrative users on Cilent-1

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/Eyax9PD.png" height="80%" width="80%" alt="Static"/>
</p>
<p>
<img src="https://i.imgur.com/XRItOc3.png" height="80%" width="80%" alt="icmpv4"/>
</p>
<p>
First create 2 Virtual Machines. The first being the domain controler (DC-1) (Windows 2022) and the second being the cilent (Cilent-1) (Windows 10). Then set the DC-1's NIC Private address to be static. This will keep the IP address from changing. Next check that the connection is flowing between the VM's by pinging DC-1's private IP address (ping -t (ip.address)). It will show that the connection is timed out. To fix this, log in under the Domain Controler (DC) and go to it's firewall to enable those profile whose protocol is ICMPV4. Once done, go back into Cilent-1's desktop and ping DC-1 again to see the connection flowing.
<p>
<br />
  
  <h2>Install Active Directory</h2>
  
<p>
<img src="https://i.imgur.com/OyWr8DE.png" height="80%" width="80%" alt="ADInstall"/>
</p>
<p>
<img src="https://i.imgur.com/pEfnWxA.png" height="80%" width="80%" alt="Restartlogin"/>
</p>
<p>
  I logged into DC-1 to install Active Directory Domain Services and set up a new forest as stepdomain.com. Once the system restarted, I was able to log into DC-1 as stepdomain.com\labuser. 
</p>
<br />


  <h2>Create Admin and Normal User Account in AD</h2>
  
<p>
<img src="https://i.imgur.com/OZIRAko.png" height="80%" width="80%" alt="TC"/>
</p>
<p>
<img src="https://i.imgur.com/COEx759.png" height="80%" width="80%" alt="TCProp."/>
</p>
<p>
From DC-1, I went into Active Directory User and Computers (ADUC) and created organizational units for ADMIN and EMPLOYEES. Next, I needed an admin's account and although the system had already provided me with some, I created a new adminstrative account. Tom Cool became the user. In order to make the user an actual domain admin, I went into the properties and under members of, added the "Domains Admin" group. Once I did that, I logged off and logged back on, but under the user created.
</p>

 <h2>Join Cilent-1 and Setup Remote Desktop</h2>
 
<p>
Cilent-1 needed to be joined to stepdomain.com, so it's virtual network interface card (NIC), had to be changed so that it's DNS was set to the same domain controller that runs DC-1's ip address. 
</p> 
<p>
<img src="https://i.imgur.com/hh3oZDb.png" height="80%" width="80%" alt="dns."/>
</p>
<p>
<img src="https://i.imgur.com/FSqnvL9.png" height="80%" width="80%" alt="dnsset"/>
</p>
<br />
<p>
Next the remote desktop was setup for nonadminstrative users. Cilent-1 needed to be joined to stepdomain.com, so it's virtual network interface card (NIC), had to be changed so that it's DNS was set to the same domain controller that runs DC-1's ip address. 
</p> 
<p>
<img src="https://i.imgur.com/1jXicZS.png" height="80%" width="80%" alt="domainusers"/>
</p>
<p>
Access was then given to all users within the domain group. 
</p> 
<br />

<p>
<img src="https://i.imgur.com/JzAnJCO.png" height="80%" width="80%" alt="createaccounts"/>
</p>
<p>
Lastly Powershell ISE was ran as an administrator in order to run a script that created 1000 accounts. These were observed in Active Directory User and Computers and tested on by logging into Cilent-1 with one of the new accounts. I came across an error that denied the account access as an admin. This required me to open up properties of that account and under Members Of, add the Domain Admin group.
</p> 
<br />
