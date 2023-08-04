<p align="center">
<img src="https://i.imgur.com/4i1Qj2R.png" alt="Microsoft logo"/>
</p>


<h1>Active Directory - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install Actove Directory with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used </h2>

- Windows 10 Pro</b> (21H2)
- Window Server

<h2>List of Prerequisites</h2>

- Set up Resources for DC-1 and Client-1 in Azure
- make sure there is a connection between the two servers.
- Set the Domain Controller's NIC Private IP address to be static. 


<h2>Install Active Directory</h2>

<p>
<img src="https://i.imgur.com/o4jshqQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/sY5ZGl6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Login to DC-1 and install Active Directory Domain Services
- Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
- Restart and then log back into DC-1 as user: mydomain.com\labuser

</p>
<br />

<h2>Create Organizational Units</h2>

<p>
<img src="https://i.imgur.com/XrhoCbj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/Bw45aAG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/LPtQm9r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”
- Create a new OU named “_ADMINS”
- Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”
- Add jane_admin to the “Domain Admins” Security Group
- Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin”
- User jane_admin as your admin account from now on


</p>
<br />

<h2>Join Client-1 to domain</h2> 

<p>
<img src="https://i.imgur.com/PlqPCBO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DXqB8q8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/WABpQIN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address
- From the Azure Portal, restart Client-1
- Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart)
- Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain


</p>
<br />

<h2>Setup Remote Desktop for non-administrative users on Client-1 </h2> 

<p>
<img src="https://i.imgur.com/49lXIqq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Log into Client-1 as mydomain.com\jane_admin and open system properties
- Click “Remote Desktop”
- Allow “domain users” access to remote desktop
- You can now log into Client-1 as a normal, non-administrative user now


</p>
<br />

<h2>Create a bunch of additional users and attempt to log into client-1 with one of the users </h2> 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Login to DC-1 as jane_admin
- Open PowerShell_ise as an administrator
- Create a new File and paste the contents of the script into it 

</p>
<br />
