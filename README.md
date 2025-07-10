<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This repository provides a step-by-step guide to installing osTicket, an open-source support ticket system, on a Windows 10 virtual machine hosted in Microsoft Azure. The tutorial covers setting up the necessary prerequisites, including IIS, PHP, and MySQL, and configuring osTicket for use.
<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>OverviewSteps</h2>

- Setup a virtual machine in Azure
- Install the OS Ticket requirements
- Install OS Ticket itself




<h2>Installation Steps</h2>

![OS Ticket Setup](https://github.com/user-attachments/assets/afe23a0e-6341-4de7-a9b4-2c11f976977a)

*1. Create a virtual machine in Azure (OSTicket-VM)*

![OS Ticket Setup 2](https://github.com/user-attachments/assets/8e89d4d6-e755-45f5-93fe-1d744b530ccc)

*2. Find the public IP address (20.186.18.217)*

![OS Ticket Setup 3](https://github.com/user-attachments/assets/20c22800-c6f1-449c-9228-56af40441397)

*3. Log in to the virtual machine using Remote Desktop Connection and the username and password created when setting up the virtual machine*

   
![OS Ticket Setup 4](https://github.com/user-attachments/assets/2215e6b7-5421-45f5-b4b9-004ba39996f8)

*4. Within the virtual machine (OSTicket-VM), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies. These files were provided as part of the lab.*


![OS Ticket Setup 5](https://github.com/user-attachments/assets/8cac0e3c-3d5e-4824-870e-16ab30bcaeea)

*5. Install / Enable IIS in Windows WITH CGI*
   
   *Open Windows Features through the Control Panel - Programs - Windows Features
   Navigate to Internet Information Services - Worldwide Web Services - Application Development Features-
   Turn on the CGI*

![OS Ticket Setup 6](https://github.com/user-attachments/assets/8a24e127-72f5-4ae9-a942-a19f532992ab)

*6. Install the PHP Manager for IIS found within the OS Ticket installation folder*

![OS Ticket Setup 7](https://github.com/user-attachments/assets/a9a4e433-4e90-4d23-a64e-3e9ff0ad0688)

*7. Install the IIS URL Rewrite Module*

![OS Ticket Setup 8](https://github.com/user-attachments/assets/c6536fd6-d0f2-4adf-8dfb-d24b225ab910)

*8. Create the directory C:\PHP*

![OS Ticket Setup 9](https://github.com/user-attachments/assets/7166cfaa-c417-4809-8034-772fe2c8a199)



 *9. From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder*
   
![OS Ticket Setup 10](https://github.com/user-attachments/assets/b2661ca0-77da-4f80-84f5-52c0673d9fd1)

*10. Run and setup the VC redistributable file*

![OS Ticket Setup 11](https://github.com/user-attachments/assets/0cd9580b-8125-42ff-9959-abad56e885ab)

*11. Run and setup MySQL*
*Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->* 
*Username: root*
*Password: root*


![OS Ticket Setup 12](https://github.com/user-attachments/assets/c2923a73-d8c1-46c3-8fc4-4be7caa9d751)


*12. Open IIS as an Admin*



![OS Ticket Setup 13](https://github.com/user-attachments/assets/9b705a8a-88ba-4ecc-b4c9-37b4907d76a1)

*13. Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)*



![OS Ticket Setup 14](https://github.com/user-attachments/assets/4c4c0858-39d9-486b-bd25-abd8cdcedb57)


*14. From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip”*

![OS Ticket Setup 15](https://github.com/user-attachments/assets/797b172a-fc82-4c9a-908f-3ae68bf99f62)


 *15. Copy the “upload” folder into “c:\inetpub\wwwroot”*

![OS Ticket Setup 16](https://github.com/user-attachments/assets/e234aa6a-e213-468f-9f88-a0287105904f)
 *16. Rename “upload” to “osTicket”*
![OS Ticket Setup 17](https://github.com/user-attachments/assets/e77602bc-14a5-4f99-9827-8a6777300ce7)

*17. *Reload IIS*

*Go to sites -> Default -> osTicket*
*On the right, click “Browse *:80”*


![OS Ticket Setup 18](https://github.com/user-attachments/assets/b6933a24-3c9e-49e6-ac03-9ac797a9b528)

*Double-click PHP Manager*
*Click “Enable or disable an extension”*
*Enable: php_imap.dll*
*Enable: php_intl.dll*
*Enable: php_opcache.dll*


![OS Ticket Setup 19](https://github.com/user-attachments/assets/644ae224-bc86-4857-b28d-d4b0c0e57681)

*Rename: ost-config.php*
*From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php*
*To: C:\inetpub\wwwroot\osTicket\include\ost-config.php*


![OS Ticket Setup 20](https://github.com/user-attachments/assets/f4389faa-a498-4c31-a4a8-24ddc977c6f3)


![OS Ticket Setup 21](https://github.com/user-attachments/assets/5f26fb23-d6aa-4ad2-b1f1-8626a039d438)

*Assign Permissions: ost-config.php*
*Disable inheritance -> Remove All*
*New Permissions -> Everyone -> All*


![OS Ticket Setup 22](https://github.com/user-attachments/assets/51c9e3ea-09bc-4fc3-a9d6-3ea78d67a060)


*Continue Setting up osTicket in the browser*

![OS Ticket Setup 23](https://github.com/user-attachments/assets/b2cd897c-c8b8-43ed-9f4b-375bface2359)


*From the “osTicket-Installation-Files” folder, install HeidiSQL.*
*Open Heidi SQL*




![OS Ticket Setup 24](https://github.com/user-attachments/assets/e31aa7cd-5659-4741-ba8b-560c886df3f9)

*Create a new session, root/root*



![OS Ticket Setup 25](https://github.com/user-attachments/assets/5dfce464-9ece-4ed8-b513-3d2c157bfe6d)

*Connect to the session*
*Create a database called “osTicket”*



![OS Ticket Setup 26](https://github.com/user-attachments/assets/230d0b79-6bcb-41d6-a534-798bd2f487c9)


*Continue Setting up osTicket in the browser*
*MySQL Database: osTicket*
*MySQL Username: root*
*MySQL Password: root*
*Click “Install Now!”*





![OS Ticket Setup 27](https://github.com/user-attachments/assets/d3cfe18c-220e-4aef-a2b5-2807749ab2f2)

*Congratulations! osTicket should now be installed*


![OS Ticket Setup 28](https://github.com/user-attachments/assets/22ecefb0-a186-46bc-8788-a55e7a3a7ddd)

*Browse to your help desk login page: http://localhost/osTicket/scp/login.php*

![Os Ticket Setup 29](https://github.com/user-attachments/assets/9dbd2b87-3930-4fee-a74c-74955092a4bd)

*Login to osTicket*


