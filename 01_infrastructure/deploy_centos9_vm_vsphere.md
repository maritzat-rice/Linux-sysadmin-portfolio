## Deploy a New CentOS Stream 9 Virtual Machine on vSphere

## Objective
Provision a new CentOS Stream 9 virtual machine in the vSphere environment following organizational naming conventions and resource requirements. This task demonstrates foundational SysAdmin skills including VM provisioning, hardware configuration, ISO mounting, OS installation, and asset inventory documentation.

## Summary
Created a new VM named **dev-app-XX1.XXXXX.XX1** on host **10.X.XX.90** using datastore **DS‑01**.  
Configured CPU, memory, disk, network, and ISO settings according to requirements.  
Installed CentOS Stream 9, completed initial OS setup, and added the VM to the Asset Tiger inventory with full hardware details.

---

## Completed Tasks

### 🔹 1. Accessed vSphere Environment
- Logged into vSphere  
- Navigated to host: **10.X.XX.90**


<img src="https://github.com/user-attachments/assets/fa7793ff-35f7-46db-a658-6fcbdafa6777" width="125"/>



### 🔹 2. Created New Virtual Machine
Steps:
1.	**New Virtual Machine → Create a New Virtual Machine**


<img src="https://github.com/user-attachments/assets/26a9980f-9355-476a-9db2-72b20186f3dd" width="125"/>


2.	VM Name: **dev-app-XX1.XXX.XXX1**


<img src="https://github.com/user-attachments/assets/697f6149-35ae-47dd-b5fc-08a46f22c2d8" width="200"/>


3. Location: *default vCenter location (no specific requirement provided)*
4. Compute Resource: **10.X.XX.90**


<img src="https://github.com/user-attachments/assets/156bc495-a9a1-45e3-9fb3-29f4250a61b0" width="200"/>

5. Compatibility checks: ✔ Successful

---

### 🔹 3. Selected Storage
- Datastore: **DS‑01**


<img src="https://github.com/user-attachments/assets/b0525a94-b0af-46ef-bc7f-4a7877f0e3d8" width="250"/>

- Noted expected warning: *“You don't have profile-driven storage view privileges”*
  (normal for apprenticeship access)

<img src="https://github.com/user-attachments/assets/e3ca4857-684d-4b6d-8d60-19716cdb8896" width="250"/>

---

### 🔹 4. Selected Guest OS
- Guest OS Family: **Linux**
- Guest OS Version: **Red Hat Enterprise Linux 9 (64-bit)**  
  *(Correct choice because CentOS Stream tracks RHEL)*

<img src="https://github.com/user-attachments/assets/7567da5d-4ab4-4a5e-b3b9-fc64a973c43f" width="250"/>

---

### 🔹 5. Customized VM Hardware
- **CPU:** 1 vCPU  
- **Memory:** 1 GB  
- **Hard Disk:** 20 GB (Thin Provisioned)  
- **Network Adapter:** YT-Intran-VLAN  
- **CD/DVD Drive:** Datastore ISO File  
  - ISO Path: `/DS-01/ISO Images/CentOS-Stream-9-latest-x86_64-dvd1.iso`
  - Connect at Power On: ✔ Enabled

Reviewed configuration → **Finish**

<p>
<img src="https://github.com/user-attachments/assets/7e55bc57-2025-490f-b6e4-042134670059" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/af3de065-7288-4050-905f-4899ab553cdd" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/dc530e05-0a18-4780-9edf-c0808986af5f" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d0a867ad-d416-4905-a2fa-b3906647cd62" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/6ab0b976-c835-4ef9-b935-dbdf563aff7e" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/b7202b93-97b4-4f6a-a4b0-a66a350a7098" width="300"/>
<p>


---

### 🔹 6. Powered On VM & Launched Web Console
- Booted into CentOS Stream 9 installer  
- Selected language → Continue

<p>
<img src="https://github.com/user-attachments/assets/2cd82e89-ad6a-42f8-9435-67c91ca59ea0" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d5890730-cd5c-48d1-9b23-7ebef73e065a" width="300"/>
<p>

---

## CentOS Installation Steps

### 🔹 7. Addressed Installation Summary Requirements
Errors shown:
- Root password disabled  
- No user created  
- Installation destination not configured  


<img src="https://github.com/user-attachments/assets/8f5270c4-1e3b-4e67-bf6e-f19890c52eaf" width="300"/>

### 🔹 8. Set Root Password
- Created password: **Passw0rd!**
- Did **not** lock root account  
- Did **not** allow root SSH login without password


<img src="https://github.com/user-attachments/assets/78a5fbd7-2c4a-4082-8332-a688bffe68bb" width="300"/>


### 🔹 9. Created Initial User
- Full Name: **Admin User**  
- Username: **adminuser**  
- Password: **XXX1XXX**


### 🔹 10. Configured Installation Destination
- Selected VMware Virtual Disk  
- Clicked **Done** to clear storage error

<p>
<img src="https://github.com/user-attachments/assets/55d1456f-9114-4420-8761-10863a172217" width="175"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/fca9eb95-331d-4e4c-938c-49554492b552" width="300"/>
<p>

### 🔹 11. Begin Installation
- Installation completed successfully  
- Selected **Reboot System**

<p>
<img src="https://github.com/user-attachments/assets/9078fafd-1a19-4266-a5e2-0147a5df3840" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/fabefe57-a674-4572-a791-f8b32082c1ef" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ac70bbbc-12c4-45a7-a52f-69b63f2afb8a" width="300"/>
<p>

---

## Post‑Install Setup

### 🔹 12. Completed Initial GNOME Setup
- Privacy: default  
- Online Accounts: skipped  
- User creation confirmed  
- Arrived at GNOME desktop

<img src="https://github.com/user-attachments/assets/991b713e-62b9-49a0-bf94-8054c7e1d5da" width="300"/>

---

## Asset Tiger Inventory Update

Added VM to Asset Tiger with required fields:
- Serial Number  
- IP Address  
- MAC Address  
- CPU  
- Memory  
- OS  
- Owner  
- Site  
- Status  
- Category  
- Location  

<p>
<img src="https://github.com/user-attachments/assets/1c820606-7539-465c-9997-1baeb635f263" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ab2f96fe-0ab0-44ee-b781-c8edf285198d" width="300"/>
<p>

---

## Result
The VM ** dev-app-XX1.XXX.XXX1** was successfully provisioned, configured, installed, and added to the asset inventory.  
This completes the full lifecycle of deploying a new Linux server in a virtualized environment.


