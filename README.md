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
- Create an Admin and Normal User Account in Active Directory
- Join Client VM to my new domain
- Setup Remote Desktop for non-admin users on Client-1 VM


<h2>Deployment and Configuration Steps</h2>

<p>
<img src ="https://github.com/bryuan47/configure-ad/assets/76184628/fdf4fb04-e996-42c7-98ad-bd9e60d20223"
>
</p>
<p>
1) First and foremost, I created two Virtual Machines through Azure Portal one named DC-1 and another named Client-1. DC-1 would serve as the Domain Controller and the other as a client machine. I made sure DC-1's NIC Private IP address to static so it does not change and make both VMs on the same virtual network. Lastly, when setting up both VMs DC-1 was initiated with Windows Server 2022 and Client-1 was initiated with Windows 10 for operating systems. 
</p>
<br />



<p>
<img src="https://github.com/bryuan47/configure-ad/assets/76184628/de025f48-54d1-4471-971c-05315cd54b25"
/>
</p>
<p>
2) Next, I ensured the connectivity between the two machines by simply pinging DC-1's private IP address while logging into Client-1's virtual machine. Using the "ping -t (IP address)" command. As shown in the example image above from IONOS.com.
</p>
<br />


<p>
<img src="https://github.com/bryuan47/configure-ad/assets/76184628/ce3faee3-99a0-4812-90a0-755c5b784dfa"
/>
</p>
<p>
3) To install Active Directory, I logged into DC-1's virtual machine and installed Active Directory Domain Services. Then promote the machine to a Domain Controller and set the new environment as "mydomain.com". 



<p>
4) Next, create an admin and normal user accounts. Find through the start menu Active Directory Users and Computers then create a new organizational unit called "Employees" and "Admins". In those new Orgnzaotional Units (OU) create new users by adding them to the "Employee" OU and "Admins" OU.
  Now if you log out of DC-1 and log back in as an admin using the credentials you just created as an administrator. 
</p>


<p>
5) The next task is to connect Client-1 to the Domain Controller. I accomplished this by first changing Cient-1's DNS Setting to DC-1's private address in the Azure Portal. Then restart the machine and log back in to join the Domain Controller. 
</p>


<p>
6) Lastly, to be able to log in to Client-1 as a normal user and not an administrator login to Client-1 and first select system properties. Then select "Remote Desktop" and allow "Domain users". 
</p>



<br/>
