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

<h2> Deployment and Configuration Steps</h2>

- Step 1 - Create Two Vitural Machines making sure that they are both in the same V-Net, One will be running Windows Server the other Windows 10.
- Step 1.5 - Set the VM that is running Windows server to have a static Private IP Address. 
- Step 2 - Ensure proper communcations between both VMs (Ping from Windows 10 to Windows Server.) 
- Step 3 - Open Windows Server's firewall to all ICMPv4 echo request (WF.MSC)  (Imbound Rules/filter by Protocol/Icmpv4)(Core Networking Diagnostics - ICMP Echo Request- There are two 
  of the one has a private profile and the other has a domain profile. 
- Step 4 - Go to Server manager, Add Roles and Features and check Active Directory Domain Services, Add new Forest when making the Domain name. Reconnect when done be cautious sometimes the I.P changed from this.
- Step 5 - From now on log on with the website name and the user name (websitename.com\username.)
- Step 6 - Go to active directory users and computers( this can be typed into the search bar or in the server manger if you click tools in the top right.
- Step 7 - Click the name of the website made and create two Orginization units _employees and _admins (employees has to be spelled correctly needed for powershell scipt.)
- Step 8 - Create a admin user (click admin/new/user)
- Step 8.5 - Right click the name, click properties - then memeber of - add type in domain admin check the name, then click okay, apply and okay.
- Step 9 - Log off and re sign in as your admin position.
- Step 10 - Find out the Pritvate I.P Address for the the VM running the Windows Server
- Step 11 - Now we need to change the DNS settings on the VM running Windows 10 on Azure, click on the Windows 10 VM, then Network Settings, then right under Network interface/ IP configuration - click on client-1241_z1 (primary)/ IPconfig (primary) <img width="1440" alt="Screen Shot 2023-10-31 at 9 43 48 PM" src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/f6d41fed-b760-48b6-9613-9ad3b7e9a5fd">
- Step 11.5 - Once you click there it will allow you to click on DNS setting where under DNS Servers you can change it from inherit from vitural network to custom. Then type in the Windows Servers Private IP.

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
