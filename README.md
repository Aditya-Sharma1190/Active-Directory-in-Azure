<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment and Group Policy Management using Windows PowerSell in Cloud (AZURE)</h1>
implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

![image](https://github.com/user-attachments/assets/06a8dcf8-c145-4f5d-9cad-f1f72df3812a)


- we will need two VMs , one running windows server 2022 image which will be our DC (Domain Controller),DNS Server and will 
  host our domain. Other Virtual Machine will act as a client machine. 
- Next we will join Client machine to our domain. 
- Using Windows PowerShell , we will create users in our Domain Controller and we will login as one of those users on our 
  client machine.

<h2>Deployment and Configuration Steps</h2>
Setup Domain Controller in Azure<br />

Create a Resource Group AD-LAB in Azure Subscription<br />

![image](https://github.com/user-attachments/assets/ee6ea044-82fd-4e16-acc0-9fba6bd92600)

Create a Virtual Network and Subnet in Azure Subscription<br />


Create the Domain Controller VM (Windows Server 2022) named “DC-1”
● Username: labuser
● Password: Cyberlab1234
After VM is created, set Domain Controller’s NIC Private IP address to be static, so that it remains permanent and does not change as the VM is rebooted 
Log into the VM and disable the Windows Firewall (for testing connectivity)




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
