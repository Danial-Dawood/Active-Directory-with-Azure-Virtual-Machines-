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
  of the one has a private profile and the other has a domain profile. <img width="1440" alt="Screen Shot 2023-11-01 at 5 16 01 PM" src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/dd9a1e64-b41e-4a7c-b16f-43f7e1643f36">
- Step 4 - Go to Server manager, Add Roles and Features and check Active Directory Domain Services, Add new Forest when making the Domain name. Reconnect when done be cautious sometimes the I.P changed from this.(The one Highlighted it wont be installed alreayd for you) <img width="1440" alt="Screen Shot 2023-11-01 at 5 20 36 PM" src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/94f878ca-920b-4fc1-8aa5-c5dc4133b49a">
- Step 5 - From now on log on with the website name and the user name (websitename.com\username.)
- Step 6 - Go to active directory users and computers( this can be typed into the search bar or in the server manger if you click tools in the top right.
- Step 7 - Click the name of the website made and create two Orginization units _employees and _admins (employees has to be spelled correctly needed for powershell scipt.) This is what they will look like after you refresh <img width="1440" alt="Screen Shot 2023-11-01 at 5 24 17 PM" src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/a1a45e88-60f4-4394-ac93-7f50229ce571">

- Step 8 - Create a admin user (click admin/new/user)
- Step 8.5 - Right click the name, click properties - then memeber of - add type in domain admin check the name, then click okay, apply and okay.
- Step 9 - Log off and re sign in as your admin position.
- Step 10 - Find out the Pritvate I.P Address for the the VM running the Windows Server
- Step 11 - Now we need to change the DNS settings on the VM running Windows 10 on Azure, click on the Windows 10 VM, then Network 
  Settings, then right under Network interface/ IP configuration - click on client-1241_z1 (primary)/ IPconfig (primary) <img width="1440" alt="Screen Shot 2023-10-31 at 9 43 48 PM" src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/4534fbb5-544d-4773-b231-d0dd6e4370d2">

- Step 11.5 - Once you click there it will allow you to click on DNS setting where under DNS Servers you can change it from inherit from vitural network to custom. Then type in the Windows Servers Private IP.
- Step 12 - Go into the VM Running Windows 10, right click the start button at the bottom right, go to system and click on Rename this PC. Under the computer name tab the most bottom     option says to change this computer name or change it domain you will click on change.
- Step 13 - Under Member of change it from work group to domain then enter the name of the website.
- Step 14 - After entering this in it will prompt you to log in, log in with the admin account you have made on the Windows Server VM
- Step 15 - After doing so it will Restart the VM and then when you log in again log in with the same VM (both VM will be logged in witht the same admin account at this point even 
  though the admin was never made on this computer this is done by the domain being switched to the Windows Server domain. Simair to how in school you can log into any computer with 
  your credentials you dont have to make a account on every computer.)
- Step 16 - Now we need to make it so that anyone not just a admin can log into the windows 10 VM. Rigth click the start button, then go to system then go to remote decktop. At the bottom   under User accounts click (select users that can remotely access is PC)
- Step 17 - Next click Add and and type in domain users and click check names it should unline it and caps the first letters of each word. Then click okay(x2) and this will maake it so   any domain user can log on to this computer (not just a admin). This is what it looks like when your have allowed all domain users to be able to log in <img width="1440" alt="Screen Shot 2023-11-01 at 5 31 21 PM" src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/8fee186a-a27d-47ac-a3fc-bc3de6b1d5ca">


- Step 18 - Now go to the Windows Server VM, open up PowerShell as a Admin (so you much be logged into the windows server vm with the admin user we had created.) Open a new Script and    put in https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1 this scprit for making users( changed number at the top of the script from 10000 to 100 so it   doesnt just make random accounts for 30 minutes)
- Step 19 - After Running the Script you can look into the Active Directory(My domain/_employees) and you will see all the random names being created.
- Step 20 - Choose one and sign into the windows 10 VM with it( try locking it out and go into Active directory and unlock it )
- Step 20.5 - Click the name of the user go to properties and it will show you the option to lock and unlock the account <img width="1440" alt="Screen Shot 2023-10-31 at 11 32 07 PM"     src="https://github.com/Danial-Dawood/Active-Directory-with-Azure-Virtual-Machines-/assets/149525309/4250cace-d524-4cd8-93a5-5f1d31392324">
-(Real world tip) - When In active directory you can also change passwords and lock acccounts by right clicking on the name.

