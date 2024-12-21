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
- Windows 10 Pro (22H2)

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

Create a Virtual Network Active_Directory_VNET and Subnet in Azure Subscription<br />

![image](https://github.com/user-attachments/assets/d7a6d04d-d8d0-4b26-86e4-d2f31a829a4f)

Create the Domain Controller VM (Windows Server 2022) named “DC”, For resource group choose AD-LAB
● Username: labuser
● Password: Cyberuser1234

![image](https://github.com/user-attachments/assets/ca34fcd1-7802-4428-a40b-fa6c41742a4c)

![image](https://github.com/user-attachments/assets/4b652c84-b2ba-47dd-8f80-64119b1c5967)

![image](https://github.com/user-attachments/assets/a0c21344-4b01-4517-aa06-a5e57f09f51e)


Create the Client VM (Windows 10 Pro (22H2)) named “Client”, For resource group choose AD-LAB
● Username: labuser
● Password: Cyberuser1234

![image](https://github.com/user-attachments/assets/1c619ebe-2552-49fd-9325-f8c175834482)

![image](https://github.com/user-attachments/assets/150176d9-178d-4732-acfa-d51bb393d897)

![image](https://github.com/user-attachments/assets/abe2da51-632a-4b44-80c1-33d863192e71)

![image](https://github.com/user-attachments/assets/56adc63e-eb23-487c-aa38-0f037eafd15e)

After VM are created, set Domain Controller’s(DC VM) NIC Private IP address to be static, so that it remains permanent and does not change as the VM is rebooted <br />
As, the Private IP for DC will be used by Client VM as it's DNS<br />

![image](https://github.com/user-attachments/assets/08a69e8c-fd9f-49eb-ac77-4ea5c6dca9f5)

Log into the DC VM and disable the Windows Firewall (for testing connectivity)

![image](https://github.com/user-attachments/assets/f404886b-2e20-4b5e-9361-8c43224bb7e9)

![image](https://github.com/user-attachments/assets/de43ba60-c094-48cd-b623-2788e3bd15ff)

Next, as we want our Client VM to join our Domain : mydomain.com , we will change the network settings of Client VM and in DNS we will paste the Private IP of the DC VM . Since to resolve mydomain.com Client VM needs the Private IP of the DC VM that is hosting the Domain mydomain.com

![image](https://github.com/user-attachments/assets/71be74c6-99e5-4744-84e2-31f01181b50d)

Next to test connectivity login to Client VM and ping the Private IP of DC VM, It should ping

![image](https://github.com/user-attachments/assets/14f8cd6c-4b3b-48ed-9997-211bd5e6bf44)

![image](https://github.com/user-attachments/assets/fbab6602-0c6d-42ea-97d9-3fd7f94d4a9b)

<h2>Deploying Active Directory</h2>

Connect to DC VM using RDP , In server manager >> Add roles and features >> Select Active Directory Domain Services 

![image](https://github.com/user-attachments/assets/b4261277-8138-48b0-90f2-1c4330720ac0)

![image](https://github.com/user-attachments/assets/8596750c-57a9-4bdc-9db1-c84645f4015a)

Next , we want to promote DC VM as a Domain controller to host mydomain.com . In DC VM open Server Manager , click on notifications in the top right corner >> promote this server to a Domain Controller 

![image](https://github.com/user-attachments/assets/4ed7fa81-a7d7-48ef-a2e3-8e9a54de7e56)

![image](https://github.com/user-attachments/assets/8894ff79-39ae-481e-b5e6-67a3e9f42bb7)

![image](https://github.com/user-attachments/assets/7d28e896-ee7a-42b7-8856-365b971dea4f)

![image](https://github.com/user-attachments/assets/5de17d59-beec-492e-bf3d-b25d691efdff)

The RDP session will terminate as the VM will restart , since DC VM is a domain controller now , in order to RDP we will have to provide context <br />

username : mydomain.com\labuser<br />
password : Cyberuser1234<br />

<h2>Create a domain admin user </h2>

Connect to DC VM using RDP<br />
username : mydomain.com\labuser<br />
password : Cyberuser1234<br />

In Windows Administrative tools >> Active Directory Users and Computers 

![image](https://github.com/user-attachments/assets/dab4ac33-5f45-42b4-8cfb-704af30a50df)

We will create a new Organizational Unit _EMPLOYEES ( can be anything , devices, group, users. Used for organizing)
























