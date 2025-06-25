# Active Directory Lab – Windows Server 2019

This lab demonstrates the creation of an Active Directory Domain Services (AD DS) environment from scratch using Windows Server 2019 and a Windows 10 client within a VirtualBox setup. It simulates real-world tasks performed by IT administrators, including domain controller setup, DNS configuration, GPO deployment, and client machine domain integration.

---

## Lab Setup Overview

- **Platform:** VirtualBox
- **Server OS:** Windows Server 2019
- **Client OS:** Windows 10
- **Roles Installed:** Active Directory Domain Services (AD DS), DNS
- **Network Type:** Internal Network (Static IPs)

---

## Step-by-Step Walkthrough

### 1. Create the DC01 Virtual Machine
Configured a new VM in VirtualBox and mounted the Server 2019 ISO to begin installation.

![01 - Creating DC01 VM](https://github.com/user-attachments/assets/71f50f53-9da4-42f0-89b1-c251a439cf05)

### 2. Select Windows Server 2019 Standard Evaluation (Desktop Experience)
Chose the GUI-enabled edition of Server 2019 during setup.

![02 - Selecting Windows Server 2019 Standard Evaluation](https://github.com/user-attachments/assets/c0ca4133-33a2-428a-91b6-aa93580bad8b)

### 3. Complete Installation of Windows Server 2019
Waited for the system to install, update, and reboot.

![03 - Installing Windows on Server 2019](https://github.com/user-attachments/assets/cee360bd-3511-4377-9a84-1c7614063e12)

### 4. Configure Computer Name: `DC01`
Renamed the server to `DC01` for clarity within the environment.

![04 - Properties For DC01](https://github.com/user-attachments/assets/1459db8a-f820-4a96-add1-034a7608078f)

### 5. Assign a Static IP to DC01
Set a static IP (e.g., `192.168.1.10`) to ensure DNS and client connectivity remain stable.

![05 - Configuring Static IP of DC01](https://github.com/user-attachments/assets/4aec27c2-784a-4145-9c1c-6f1bcd4ceabd)

### 6. Install the AD DS Role
Used Server Manager to install the Active Directory Domain Services role.

![06 - Installing AD DS](https://github.com/user-attachments/assets/b1ae8dc1-02c3-446a-9859-c0cc4fd1da3d)

### 7. Perform Prerequisite Check
Verified all conditions for domain controller promotion were satisfied.

![07 - Prerequisite Check Before Promoting DC](https://github.com/user-attachments/assets/4ef17424-751d-4ee4-a2b5-bb03b5284f5b)

### 8. Promote DC01 to a Domain Controller
Configured a new forest with the domain name `iylabs.local`.

![08 - Successfully promoted to Domain Controller](https://github.com/user-attachments/assets/ad8f9a79-ba8a-4f84-ab91-7527dfd7a166)

### 9. Confirm Domain Promotion
Restarted the server and confirmed successful domain controller promotion.

![09 - Verifying Domain iylabs local](https://github.com/user-attachments/assets/4e876bf1-51c6-42c3-9f72-0848ddbe94e7)

### 10. Create Organizational Unit: `IT_Users`
Created a new OU in Active Directory Users and Computers to organize user accounts.

![10 - Creating OU](https://github.com/user-attachments/assets/557b1ff2-3938-4142-8b2d-d0fc2f1e76a8)


### 11. Add Users to OU
Created two users (`Isaac Yoon`, `Joseph Smith`) within the `IT_Users` OU.

![11 - Adding Users to OU](https://github.com/user-attachments/assets/965e9aeb-cbcc-407f-9cfb-ef989c3ee10d)


### 12. Launch Group Policy Management Console (GPMC)
Opened GPMC to configure domain-linked Group Policy Objects.

![12 - Viewing IT_Users OU in Group Policy Management](https://github.com/user-attachments/assets/da7d3a94-0bfd-4937-9742-ed62e9824f4f)


### 13. Create GPO: “Disable Control Panel – IT Users”
Created a new GPO linked to `IT_Users` for restricting Control Panel access.

![13 - Creating GPO to Disable Control Panel for IT_Users](https://github.com/user-attachments/assets/dfd87527-decc-4f2d-b483-c07d40333e73)


### 14. Verify GPO Link
Confirmed that the GPO is enabled and linked to the correct OU.

![14 - Linked GPO Confirmation - Disable Control Panel](https://github.com/user-attachments/assets/b49b9b06-1469-46ff-9f32-66ef612cd74d)


### 15. Configure GPO to Disable Control Panel
Edited the GPO to enable:  
`User Configuration → Administrative Templates → Control Panel → Prohibit access to Control Panel and PC settings`

![15 - Configuring GPO - Disable Control Panel Access](https://github.com/user-attachments/assets/ad079205-61ca-455d-8fb7-2ce582aae148)


### 16. Enable the Setting
Set the policy to **Enabled** to enforce the restriction.

![16 - Enabling GPO - Prohibit Control Panel Access](https://github.com/user-attachments/assets/bb7091ca-1687-498e-81f4-72c0665fa67d)


### 17. Prevent Registry Access via GPO
Enabled:  
`User Configuration → Administrative Templates → System → Prevent access to registry editing tools`

![17 - Configuring GPO - Prevent Registry Editing Tools](https://github.com/user-attachments/assets/151853d2-6ef0-4957-af17-ff639e057b4a)


### 18. Spin Up Windows 10 Client
Installed Windows 10 on a new VM to act as the domain client.

![18 - Spinning Up Windows 10 Client VM](https://github.com/user-attachments/assets/6c8fc862-007b-439c-99f3-791ac740aaa0)


### 19. Assign Static IP to Client
Configured a static IP (e.g., `192.168.1.20`) and set DC01 as its DNS server.

![19 - Verifying Communication - Ping from Win10 Client to DC01](https://github.com/user-attachments/assets/51f30b9f-6e79-4334-aa2a-b9571428ebbd)


### 20. Join the Client to Domain
Used system properties to join the domain `iylabs.local`.

![20 - Preparing Win10 Client - Viewing System Properties](https://github.com/user-attachments/assets/1352220a-a7ca-4032-89df-7d20781f8bd7)


### 21. Rename the Client Machine
Renamed to a meaningful hostname (e.g., `Win10Client`).

![21 - Initiating Domain Join from Win10 Client](https://github.com/user-attachments/assets/0ee35b75-d95d-482a-8a7d-7326370ff463)


### 22. Log in Using Domain Credentials
Used credentials for `jsmith@iylabs.local` to test domain logon.

![22 - Logging in with Domain User (jsmith)](https://github.com/user-attachments/assets/b9e1bd95-8e42-4238-a7c9-65ad80fd65d8)


### 23. Change Password on First Login
Prompted to reset password per default AD policy.

![23 - Prompt to Change Password on First Login](https://github.com/user-attachments/assets/17c0d0ff-15cd-430e-abf8-fe48d01e4693)


### 24. Successful Domain Login
Confirmed `jsmith` logged into the domain successfully.

![24 - Password Successfully Changed](https://github.com/user-attachments/assets/d7ca98f6-1319-463d-8f2c-6b4633d67c57)


### 25. Validate Group Policy Enforcement
Used `whoami` in Command Prompt to confirm domain context. Verified that both registry tools and the Control Panel were blocked via GPO.

![25 - Confirming Logged-in User and Admin (jsmith vs administrator)](https://github.com/user-attachments/assets/8881c7f8-075f-493f-9c4e-64e68e2f1a83)


---

## Skills Demonstrated

- Deploying and configuring Windows Server 2019
- Promoting a server to a domain controller
- Creating and managing Organizational Units
- Designing and enforcing Group Policy Objects
- Integrating Windows 10 clients into a domain
- Applying and validating GPO restrictions

---

