<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

<p>
</p>
<p>
<img src="https://i.imgur.com/6uuyCnL.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/k0cPepk.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>

 
  - Create a new Virtual Machine in Azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/Jp7M0sx.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/HzkVPA8.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

</p>
<p>

  - Create the Domain Controller VM (Windows Server 2022) named “DC-1”
  - Create Resource Group
  - Create  Virtual Network (Vnet)

</p>
<br />

<p>
<img src="https://i.imgur.com/sHcwXE9.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet.

</p>
<br />

<p>
<img src="https://i.imgur.com/RFuLT9s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Set Domain Controller’s NIC Private IP address to be static

</p>
<br />
<p>
<img src="https://i.imgur.com/bMz2pe1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Login to DC-1 using Remote Desktop Connection

</p>
<br /><p>
<img src="https://i.imgur.com/9LJDMvZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Go to Server Manager
  - Dashboard
  - "Add roles and features"

</p>
<br /><p>
<img src="https://i.imgur.com/GK7SfHe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Toggle on "Active Directory Domain Services"

</p>
<br /><p>
<img src="https://i.imgur.com/OLHMmOt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Finish Install
  - Promote this server to a domain controller

</p>
<br /><p>
<img src="https://i.imgur.com/1vbBQuG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Add a new forest
  - Name the Root domain name: BLANK.com Example: mydomain.com

</p>
<br /><p>
<img src="https://i.imgur.com/o3BVZMv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Set a password.

</p>
<br /><p>
<img src="https://i.imgur.com/haPoyTd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  -  Press Install

</p>
<br /><p>
<img src="https://i.imgur.com/FlGamLA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - The Install will cause the VM Computer to Reset.

</p>
<br /><p>
<img src="https://i.imgur.com/vjF1xoq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Log back in
  - This time with the "domain name" '.com'\'username'

</p>
<br /><p>
<img src="https://i.imgur.com/kK7CmtD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Search for "Active Directory Users and Computers"

</p>
<br /><p>
<img src="https://i.imgur.com/J4bBByo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Create a new "Organizational Unit"

</p>
<br />
<p>
<img src="https://i.imgur.com/TJ2l5Dw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Create a fake user
  - Remember the user for future login

</p>
<br />
<p>
<img src="https://i.imgur.com/IAo0Yho.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XIogS5T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/k3PBEJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/La4XgtT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/L908Hnm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Open the new user you created
  - Go to "Member of"
  - Add
  - Type Domain and Check Names
  - Select Domain Admins

</p>
<br />
<p>
<img src="https://i.imgur.com/rDaIA9z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Login back to DC-1
  - Using Admin login

</p>
<br /><p>
<img src="https://i.imgur.com/kCw8Jmn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Go to System Settings -> About
  - Rename this PC (Advanced)
  - Press Change

</p>
<br /><p>
<img src="https://i.imgur.com/YqViXpu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Toggle on Domain
  - Type in your domain.com
  - Don't click "OK" yet
</p>
<br /><p>
</p>
<br /><p>
<img src="https://i.imgur.com/D2BU3cD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/fVNsDEg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>

  - Go to Azure
  - Home->Virtual Machines->Client-1 | Networking->client_149_z1
  - DNS Servers
  - Click on Custom
  - Paste over the Private IP Address from DC-1: Found in Azure below the IP Address.
  - Save
  - Restart Client-1 VM

</p>
<br /><p>
<img src="https://i.imgur.com/fPjMpnF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Click "OK"
  - Put the Username and Password of the Admin
  - VM will restart

</p>
<br /><p>
<img src="https://i.imgur.com/CQmhUN3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Upon logging back into Client-1 as an Admin
  - Go to system-> About -> Remote Desktop
  - Click on "Select users that can remotely access this PC"

</p>
<br /><p>
<img src="https://i.imgur.com/QCNwblm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Click on Add
  - Type in Text box, "Domain Users".

</p>
<br /><p>
<img src="https://i.imgur.com/Yz3HtSC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Add in Domain Users

CONGRATS, you have set up Active Directory. Allowing access to all users to use this PC.
