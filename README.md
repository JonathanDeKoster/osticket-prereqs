<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation

This repository provides a **step-by-step guide** to installing **osTicket**, an open-source support ticket system, on a **Windows 10 virtual machine hosted in Microsoft Azure**. The tutorial covers setting up necessary prerequisites, including **IIS, PHP, and MySQL**, and configuring osTicket for use.  

This README is designed for portfolio purposes: it demonstrates not just **how** to set up osTicket, but also includes reasoning behind key steps.

---

## Environments and Technologies

- **Microsoft Azure** (Virtual Machines / Compute)  
- **Remote Desktop**  
- **Internet Information Services (IIS)**  

**Operating System:** Windows 10 (21H2)

---

## Project Overview

This guide walks you through:

1. Creating a virtual machine in Azure  
2. Installing osTicket prerequisites (IIS, PHP, MySQL)  
3. Installing and configuring osTicket  

---

## Installation Steps

### 1. Create a Virtual Machine in Azure

Create a VM named `OSTicket-VM`. This is where osTicket will be installed.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup](https://github.com/user-attachments/assets/afe23a0e-6341-4de7-a9b4-2c11f976977a)

</details>

---

### 2. Find the Public IP Address

Example: `20.186.18.217`  
This will be used for remote access.

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 2](https://github.com/user-attachments/assets/8e89d4d6-e755-45f5-93fe-1d744b530ccc)

</details>

---

### 3. Connect via Remote Desktop

Use the username and password created during VM setup to log in.

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 3](https://github.com/user-attachments/assets/20c22800-c6f1-449c-9228-56af40441397)

</details>

---

### 4. Download osTicket Installation Files

- Download `osTicket-Installation-Files.zip` to the VM desktop.  
- Unzip the folder; it should be called `osTicket-Installation-Files`.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 4](https://github.com/user-attachments/assets/2215e6b7-5421-45f5-b4b9-004ba39996f8)

</details>

---

### 5. Install / Enable IIS with CGI

- Open **Windows Features** → **Programs** → **Windows Features**  
- Navigate to **Internet Information Services → World Wide Web Services → Application Development Features**  
- Enable **CGI**  

**Why:** CGI is required for PHP to run properly with IIS.

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 6](https://github.com/user-attachments/assets/8a24e127-72f5-4ae9-a942-a19f532992ab)

</details>

---

### 6. Install PHP Manager for IIS

- Find it in the `osTicket-Installation-Files` folder and install it.  

**Why:** PHP Manager allows you to register and configure PHP with IIS easily.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 7](https://github.com/user-attachments/assets/a9a4e433-4e90-4d23-a64e-3e9ff0ad0688)

</details>

---

### 7. Install IIS URL Rewrite Module

**Why:** osTicket uses URL rewriting for cleaner links.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 8](https://github.com/user-attachments/assets/c6536fd6-d0f2-4adf-8dfb-d24b225ab910)

</details>

---

### 8. Create the PHP Directory

- Create `C:\PHP`  

**Why:** A dedicated folder keeps PHP files organized.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 9](https://github.com/user-attachments/assets/7166cfaa-c417-4809-8034-772fe2c8a199)

</details>

---

### 9. Install PHP 7.3.8

- Unzip `php-7.3.8-nts-Win32-VC15-x86.zip` into `C:\PHP`.  

**Why:** PHP 7.3 is compatible with osTicket v1.15.8.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 10](https://github.com/user-attachments/assets/b2661ca0-77da-4f80-84f5-52c0673d9fd1)

</details>

---

### 10. Install VC Redistributable

- Run and complete setup.  

**Why:** PHP depends on Visual C++ libraries to run properly.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 11](https://github.com/user-attachments/assets/0cd9580b-8125-42ff-9959-abad56e885ab)

</details>

---

### 11. Install MySQL

- Typical Setup → Launch Configuration Wizard → Standard Configuration  
- Username: `root`  
- Password: `root`  

**Why:** MySQL is used to store osTicket data.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 12](https://github.com/user-attachments/assets/c2923a73-d8c1-46c3-8fc4-4be7caa9d751)

</details>

---

### 12. Open IIS as Administrator

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 13](https://github.com/user-attachments/assets/9b705a8a-88ba-4ecc-b4c9-37b4907d76a1)

</details>

---

### 13. Register PHP in IIS

- Use PHP Manager → Register `C:\PHP\php-cgi.exe`.  

**Why:** IIS needs to know the PHP executable to run PHP scripts.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 14](https://github.com/user-attachments/assets/4c4c0858-39d9-486b-bd25-abd8cdcedb57)

</details>

---

### 14. Install osTicket Files

- Unzip `osTicket-v1.15.8.zip`  
- Copy the `upload` folder to `C:\inetpub\wwwroot`  
- Rename `upload` → `osTicket`  

**Why:** This makes osTicket accessible via the web server.  

<details>
<summary>Screenshots</summary>

![OS Ticket Setup 15](https://github.com/user-attachments/assets/797b172a-fc82-4c9a-908f-3ae68bf99f62)  
![OS Ticket Setup 16](https://github.com/user-attachments/assets/e234aa6a-e213-468f-9f88-a0287105904f)  
![OS Ticket Setup 17](https://github.com/user-attachments/assets/e77602bc-14a5-4f99-9827-8a6777300ce7)

</details>

---

### 15. Configure PHP Extensions

- Enable in PHP Manager:  
  - `php_imap.dll`  
  - `php_intl.dll`  
  - `php_opcache.dll`  

**Why:** Required by osTicket for email handling, internationalization, and performance.  

<details>
<summary>Screenshot</summary>

![OS Ticket Setup 19](https://github.com/user-attachments/assets/644ae224-bc86-4857-b28d-d4b0c0e57681)

</details>

---

### 16. Configure ost-config.php

- Rename `ost-sampleconfig.php` → `ost-config.php`  
- Assign permissions: Disable inheritance → Remove All → Add Everyone → Full Control  

**Why:** osTicket needs this file writable during installation.  

<details>
<summary>Screenshots</summary>

![OS Ticket Setup 20](https://github.com/user-attachments/assets/f4389faa-a498-4c31-a4a8-24ddc977c6f3)  
![OS Ticket Setup 22](https://github.com/user-attachments/assets/51c9e3ea-09bc-4fc3-a9d6-3ea78d67a060)

</details>

---

### 17. Set Up Database with HeidiSQL

1. Install HeidiSQL from `osTicket-Installation-Files`  
2. Create a session: Username `root`, Password `root`  
3. Create a database called `osTicket`  

**Why:** Database stores all ticketing data.  

<details>
<summary>Screenshots</summary>

![OS Ticket Setup 25](https://github.com/user-attachments/assets/5dfce464-9ece-4ed8-b513-3d2c157bfe6d)  
![OS Ticket Setup 26](https://github.com/user-attachments/assets/230d0b79-6bcb-41d6-a534-798bd2f487c9)

</details>

---

### 18. Complete osTicket Installation in Browser

- Database: `osTicket`  
- Username: `root`  
- Password: `root`  
- Click **Install Now!**  

<details>
<summary>Screenshots</summary>

![OS Ticket Setup 27](https://github.com/user-attachments/assets/d3cfe18c-220e-4aef-a2b5-2807749ab2f2)  
![OS Ticket Setup 28](https://github.com/user-attachments/assets/22ecefb0-a186-46bc-8788-a55e7a3a7ddd)

</details>

---

### 19. Access the Help Desk

- URL: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)  
- Login with your admin credentials  

<details>
<summary>Screenshot</summary>

![Os Ticket Setup 29](https://github.com/user-attachments/assets/9dbd2b87-3930-4fee-a74c-74955092a4bd)

</details>

---

✅ **osTicket is now installed and ready to use!**

