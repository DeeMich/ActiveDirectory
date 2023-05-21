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

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/Eyax9PD.png" height="80%" width="80%" alt="Static"/>
</p>
<p>
<img src="https://i.imgur.com/XRItOc3.png" height="80%" width="80%" alt="icmpv4"/>
</p>
<p>
First created 2 Virtual Machines. The first being the domain controler (DC-1) and the second being the cilent (Cilent-1). Then I set the DC-1's NIC Private address to be static. This will keep the IP address from changing. In order to check that the connection was flowing between the VM's, I ping DC-1's private IP address (ping -t (ip.address)), which showed that the connection was timed out. I then logged in under the Domain Controler (DC) and went to it's firewall to enable those profile whose protocol was ICMPV4. Once I did this, I went back into Cilent-1's desktop and ping DC-1 again to find the connection flowing.
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
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
