# Deploy Development Web Server Using Template

## Objective
Enhance Linux system administration skills by deploying a development web server from a vSphere template and performing required configuration tasks including static networking, IPA client setup, NFS mount creation, user management, and asset inventory updates.

---

## Task Summary
Deploy a development web server using the designated vSphere template. After deployment, update system configuration, apply static networking, install required packages, configure mount points, create a privileged local user, and document the server in the asset inventory system.

---

## Requirements
- Deploy VM from template  
- Configure static IP networking  
- Install **ipa-client**  
- Configure DNS and NFS mount points  
- Create local user **XXX**  
- Add user to **wheel** group  
- Update asset inventory with server details  

*(All sensitive IPs, hostnames, and organization names have been redacted.)*

---

## Steps Performed

### 1. Deploy VM from Template

- Selected cluster → **New Virtual Machine**

<img src="https://github.com/user-attachments/assets/c5bc8772-b15a-466e-86ff-76bdc8fd8f20" width="250"/>

- Chose **Deploy from Template**

<img src="https://github.com/user-attachments/assets/b4ba2e5d-600a-4d9c-8770-83572cbed8a2" width="250"/>

- Selected the correct vSphere template

<img src="https://github.com/user-attachments/assets/38d9a7ba-1713-4b10-95d8-880fe00a47d1" width="250"/>

- Named the VM: `<dev.-performance-XXX.XXX.prod1>`

<img src="https://github.com/user-attachments/assets/8a98a328-26d2-4193-9669-2eb650294706" width="250"/>

- Selected compute resource: `<mrice-cluster>`

<img src="https://github.com/user-attachments/assets/763f56d7-216d-4b8a-8fe4-5fbcaf5b3c03" width="250"/>

- Selected datastore: `"DS-01"`

<img src="https://github.com/user-attachments/assets/0666db60-d617-4e8a-899e-8d1be22d8bdd" width="250"/>

- Accepted default clone options

<img src="https://github.com/user-attachments/assets/d4c83993-fbde-4d30-8675-a3cb2d5416fd" width="250"/>

- Clicked **Finish** to begin deployment

<img src="https://github.com/user-attachments/assets/39cb54bf-7b10-4f52-8693-e9331ea29071" width="125"/>

---

### 2. Power On VM & Reset Password

- Powered on the newly deployed VM  

<img src="https://github.com/user-attachments/assets/9b4448ff-b83e-429f-81a7-ada4eca26587" width="250"/>

- Password was unknown → interrupted GRUB to enter rescue mode

<img src="https://github.com/user-attachments/assets/83cac457-e316-4ce3-a305-f60fb65c12bc" width="250"/>

- Set a new password  
- Created autorelabel file to bypass SELinux relabeling  

<img src="https://github.com/user-attachments/assets/aedae790-7847-4818-9a40-d3f4dd3b9493" width="250"/>

- Logged in successfully  
- Updated hostname to `<dev-performance.XX.XXX.prod1>`

<img src="https://github.com/user-attachments/assets/fbebfb84-8483-4cc1-b9a7-05411bd7950b" width="325"/>

---

### 3. Configure Static Networking

**Identified existing network connection:**

- nmcli con show

<img src="https://github.com/user-attachments/assets/47cfb750-79a2-4550-9742-1e4ec44ed4b9" width="250"/>

**Disabled autoconnect on the default connection:**

- nmcli con mod "<redacted-connection>" connection.autoconnect no nmcli con down "<redacted-connection>"

<img src="https://github.com/user-attachments/assets/dd84d823-2084-4531-950a-e826ea286c16" width="400"/>


**Created new static connection:**

- nmcli con add con-name static \ ifname ens192 \ type ethernet \ autoconnect yes \ ip4 "<redacted-ip>/<redacted-netmask>" \ gw4 "<redacted-gateway>" \ ipv4.dns "<redacted-dns>"

<img src="https://github.com/user-attachments/assets/2fcb7d5e-514f-4f4d-8811-272485552502" width="500"/>


**Brought connection online:**

- nmcli con up static
- Nmcli con show

<img src="https://github.com/user-attachments/assets/6e624559-de1a-4427-aca6-3deb83b2763c" width="250"/>


#### Verification

- ip a 

<img src="https://github.com/user-attachments/assets/87ae0339-ada4-41a8-882a-e599c8037889" width="350"/>


- ping -c2 <redacted-gateway> 

<img src="https://github.com/user-attachments/assets/f4cb79ae-3798-4ea2-a779-deae34ccf786" width="250"/>


- ping -c2 google.com 

<img src="https://github.com/user-attachments/assets/024bf9c0-6322-49f8-b36f-ef9e56f41bc5" width="300"/>


**Results:**  
- Static IP active  
- Gateway reachable  
- DNS resolution successful  

---

### 4. Install IPA Client

- sudo dnf install ipa-client -y 

<img src="https://github.com/user-attachments/assets/b3a5689b-31d2-4c20-a2e4-da7c2c963430" width="350"/>


- sudo ipa-client-install --mkhomedir

<img src="https://github.com/user-attachments/assets/067b42f5-f812-4ae2-84a4-26d8c3c0fdda" width="250"/>


- Entered enrollment credentials when prompted.

<img src="https://github.com/user-attachments/assets/68fb9fe8-016c-49c6-8f2f-3dd2fecd8741" width="250"/>


**Verification:**

- id mrice

<img src="https://github.com/user-attachments/assets/4c2019de-980c-431f-8d54-feb99d987fa4" width="500"/>

**IPA client installation successful.**

---

### 5. Configure NFS Mount Points

Created parent directory:
Created required mount directories:

sudo mkdir -p /nfs/incoming
sudo mkdir -p /nfs/incoming/home 
sudo mkdir -p /nfs/incoming/vhosts 
sudo mkdir -p /nfs/incoming/scripts

<img src="https://github.com/user-attachments/assets/7fd98d76-d823-4194-b551-ae0e72da3684" width="250"/>

Verified:
ls -R /nfs

<img src="https://github.com/user-attachments/assets/941dde49-fd42-4a3f-8f7b-1de205d5a310" width="150"/>

---

### 6. Create Local User

Created local user/password:
sudo useradd -m XXX 
sudo passwd XXXX

Added user to wheel group:
sudo usermod -aG wheel XXX

Verified: id XXX

<img src="https://github.com/user-attachments/assets/25a87e15-40a5-4aba-9ba1-2ba20c94c457" width="350"/>

---

### 7. Asset Inventory Update

Updated the asset inventory system with redacted fields:

- **Asset Tag ID:** MRice-Ticket 12
- **Server Name:** dev-performance-XX.XXX.prod1
- **Serial Number:** f095ce46-XXX-XXX-XXX-05bb55ea0ebd
- **Description:** dev-performance-XX.XXX.prod1  
- **Owner:** Maritza  
- **Organization:** Xplus
- **IP:** 10.X.XX.175/23
- **MAC:** 00:50:56:XX:XX:XX
- **CPU:** 1 vCPU  
- **Memory:** 1 GB  
- **Operating System:** Linux (64 bit)  
- **Status:** Active  

<p>
<img src="https://github.com/user-attachments/assets/5feb3634-b7a8-4976-b7f8-43b8e3950204" width="350"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/dad833eb-c7a7-444e-a3aa-c76b3543683f" width="350"/>
<p>

All sensitive identifiers have been removed for public display.

---

## Summary of Work Completed
- Successfully deployed development web server from vSphere template  
- Reset password and updated hostname  
- Configured static IP networking  
- Verified internal/external connectivity and DNS resolution  
- Installed and configured IPA client  
- Created NFS mount directories  
- Created local user **XXX** and added to wheel group  
- Updated asset inventory with required metadata  

**Development web server deployment completed successfully.**














