## Spin Up Web Server Using Kickstart (Automated Deployment)

## Objective
Provision a staging web server using vSphere and automate the OS installation with a Kickstart file. This task demonstrates advanced provisioning skills including VM creation, GRUB parameter injection, Kickstart automation, network configuration, DNS setup, NFS mounts, repo troubleshooting, and asset inventory documentation.

## Summary
Created a new VM named **stage-web-mr1.XX.prod1** on host **10.1.XX.XX** using datastore **DS‑01**.  
Configured hardware, mounted ISO, injected Kickstart parameters, and performed a fully automated CentOS Stream 9 installation.  
Resolved multiple post-install issues including root password reset, DNS configuration, NFS mount failures, and missing local repos.  
Completed full system setup and updated Asset Tiger inventory.

---

## Completed Tasks

### 🔹 1. Created VM in vSphere
- Hosts and Clusters → Host **10.1.XX.XX**
- **New Virtual Machine**
- Name: **stage-web-mr1.XX.XXX1**
- Folder: *XX-DC*
- Compute Resource: **10.1.XX.XX**
- Storage: **DS‑01**
- Guest OS: *Other 5.x or later Linux (64-bit)*  
  *(CentOS Stream 9 not listed)*

<img src="https://github.com/user-attachments/assets/022058c8-e06a-454d-8a86-bae01b9be2b5" width="250"/>

### Hardware Configuration
- CPU: 1  
- Memory: 1 GB  
- Disk: 20 GB (Thin Provisioned)  
- Network: YT-Intran-vlan  
- ISO: `/DS-01/ISO Images/CentOS-Stream-9-latest-x86_64-dvd1.iso`  
- Connect at Power On: ✔

<p>
<img src="https://github.com/user-attachments/assets/4ac37d21-05fd-476e-80d6-0e0996a7c20e" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/85971110-9504-408a-87e0-a34846de8ea0" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ac85ade3-2abb-405c-a4ec-703d6b357931" width="250"/>
<p>

---

## Kickstart Automated Installation

### 🔹 2. Booted Into GRUB & Injected Kickstart Parameters
- Interrupted GRUB → pressed **e**  
- Modified `linuxefi` line:

<img src="https://github.com/user-attachments/assets/564da05b-7a15-4360-b497-786ee1d0cf33" width="250"/>

ip=10.X.XXX.176::10.1.30.1:255.255.254.0::ens192:none \ inst.ks=http://10.X.XX.50/server-template-ks9.cfg

- Booted with: Ctrl + X

<img src="https://github.com/user-attachments/assets/b8b53792-3e66-4799-a56b-099a711bd2c7" width="250"/>

- Kickstart installation began automatically.

---

## Root Password Recovery (rd.break)

- Kickstart did not set a usable root password.


### 🔹 3. Performed Rescue Mode Reset

- rd.break 
- mount -o remount,rw /sysroot 
- chroot /sysroot 
- passwd 
- touch /.autorelabel 
- exit 
- exit


**Successfully logged in as root.**


<img src="https://github.com/user-attachments/assets/52a64fdd-323e-439a-9b1f-841881bc9f25" width="250"/>

---

## Network & Hostname Configuration

### 🔹 4. Verified Network
- ip a 
- ip route 
- nmcli con show

<p>
<img src="https://github.com/user-attachments/assets/d818fec7-5faf-482d-882e-fc184f309e7d" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/adc7d867-201d-4db8-9173-c38e96eaddd2" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/83a00d6a-117c-46fb-97ef-d102abf594eb" width="250"/>
<p>

### 🔹 5. Set Hostname
- hostnamectl set-hostname stage-web-mr1.XX.XXXX1 
- exec bash 
- hostname

<img src="https://github.com/user-attachments/assets/954c7d8f-8b00-42b2-87a5-ffd0fac8abb6" width="250"/>

### 🔹 6. Enabled Autoconnect
- nmcli con mod ens192 connection.autoconnect yes 
- nmcli con up ens192

<img src="https://github.com/user-attachments/assets/4140ff90-6090-474e-94ba-8d727d630b1a" width="250"/>

---

## DNS Configuration

**Added DNS servers:**

- nmcli con mod ens192 ipv4.dns "10.X.XX.13 10.X.XX.15" 
- nmcli con mod ens192 ipv4.ignore-auto-dns yes 
- nmcli con up ens192

<img src="https://github.com/user-attachments/assets/8c7377d3-fa93-422d-b076-ffa684a8cdd6" width="250"/>

**Verified:**
- cat /etc/resolv.conf


**Tested:**
- ping -c3 ipa.XX.dev


---

## /etc/hosts Configuration

**Added required entries:**
- 10.1.XX.XX vcenter.sandbox.prod 
- 10.1.XX.XX ipa.XX.dev 
- 10.1.XX.XX dev-nagios.XX.prod1 
- 10.1.XX.XX stage-foreman.XX.prod 
- 10.1.XX.XX stage-bacula.XX.prod 
- 10.1.XX.XX dev-ansible.XX.prod1 dev-ansible 
- 10.1.XX.XX stage-bastion.XX.prod1 stage-bastion 
- 10.1.XX.XX nfs-dev.XX.prod1 
- 10.1.XX.X76 stage-web-mr1.XX.prod1 stage-web-mr1

<img src="https://github.com/user-attachments/assets/a4647f29-d19b-4261-aab5-2b594561f23c" width="250"/>

---

## NFS Mount Setup

### 🔹 7. Created Mount Directories
- mkdir -p /nfs/incoming/home 
- mkdir -p /nfs/incoming/vhosts 
- mkdir -p /nfs/incoming/scripts

<img src="https://github.com/user-attachments/assets/ce324b1a-b2b9-4e64-a74b-98df9d0e7f66" width="250"/>

### 🔹 8. Updated /etc/fstab

- 10.X.XX.148:/nfs/share/vhosts/ /nfs/incoming/vhosts nfs defaults 0 0 
- 10.X.XX.148:/nfs/share/home/ /nfs/incoming/home nfs defaults 0 0 
- 10.X.XX.148:/nfs/share/scripts/ /nfs/incoming/scripts nfs defaults 0 0

<img src="https://github.com/user-attachments/assets/73bb1945-fd36-480e-aaad-66a638855d8c" width="250"/>

### 🔹 9. Initial Mount Failure

**Errors:**
- “bad option”
- “systemd still uses old version”
- “need mount.<type> helper”

<img src="https://github.com/user-attachments/assets/a5595b2c-095d-44d6-9f5b-54d1a806380e" width="250"/>

### ✔ Fix: Install NFS Utilities

**dnf install -y nfs-utils**

---

## Repo Troubleshooting (Kickstart Missing Local Repos)

- Kickstart did **not** create local repo files.  
- DNF attempted to reach CentOS Stream online mirrors → unreachable.

<img src="https://github.com/user-attachments/assets/8f1fe7e8-6c43-474f-a167-be1d9cb10c7f" width="300"/>


### 🔹 10. Mounted ISO Manually

- mkdir -p /mnt/iso 
- mount /dev/sr0 /mnt/iso 
- ls /mnt/iso

<p>
<img src="https://github.com/user-attachments/assets/842540f0-a3af-4de4-91f0-309ffc32f293" width="200"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/93f4fcc1-20dd-4fcd-adf9-2f138d15b5f6" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ca7374fb-c89d-4f40-b046-3c11ed7584b2" width="250"/>
<p>


### 🔹 11. Created Local Repo Files

**BaseOS**
vi /etc/yum.repos.d/baseos-local.repo 

<img src="https://github.com/user-attachments/assets/8379d68c-91ef-4c02-83c0-5260953c7463" width="250"/>

[baseos-local] 
name=BaseOS Local Repo 
baseurl=file:///mnt/iso/BaseOS 
enabled=1 
gpgcheck=0

<img src="https://github.com/user-attachments/assets/64d3625d-61dd-4e10-b718-d612ece93ea3" width="200"/>

**AppStream**
vi /etc/yum.repos.d/appstream-local.repo 

<img src="https://github.com/user-attachments/assets/3274bde0-66b6-4b11-a7ce-31577237d6bc" width="300"/>

[appstream-local] 
name=AppStream Local Repo 
baseurl=file:///mnt/iso/AppStream 
enabled=1 
gpgcheck=0

<img src="https://github.com/user-attachments/assets/3412f25d-bfce-4575-ab6a-ea42a2d54b8b" width="200"/>

### 🔹 12. Disabled Internet Repos which pointed to CentOS Stream online mirrors which the environment could not reach.

- sed -i 's/enabled=1/enabled=0/g' /etc/yum.repos.d/centos.repo
- sed -i 's/enabled=1/enabled=0/g' /etc/yum.repos.d/centos-addons.repo


### 🔹 13. Installed NFS utilities
- dnf install -y nfs-utils

<img src="https://github.com/user-attachments/assets/87ab4d92-8ae5-41f8-9787-43c0f82600f5" width="250"/>


### 🔹 14. Mounted NFS Shares
- systemctl daemon-reload 
- mount -a 
- df -h | grep nfs

<img src="https://github.com/user-attachments/assets/4abe2790-a822-41e3-93b6-4ecb47315bc8" width="250"/>

**All NFS shares mounted successfully.**

---

## Asset Inventory Update

**Added server to Asset Tiger:**

- **Name:** stage-web-mr1.XX.prod1  
- **Serial:** f095ce46-59d5-4b1e-ba75-05bb55ea0ebd  
- **IP:** 10.X.XX.176  
- **MAC:** 00:50:56:8b:a6:2f  
- **CPU:** 1  
- **Memory:** 1 GB  
- **OS:** CentOS Stream 9  
- **Status:** Active  
- **Description:** Spin up web server using Kickstart  

<p>
<img src="https://github.com/user-attachments/assets/3a1e9aec-e1f7-4902-a9db-8b8235f029b6" width="300"/>
<p>

<p>  
<img src="https://github.com/user-attachments/assets/c687cf17-a702-4932-aad0-c099313fba9f" width="300"/>
<p>

---

## Result

The VM **stage-web-mr1.XX.prod1** was successfully provisioned using Kickstart automation.  
All network, DNS, NFS, and repo configurations were completed.  
The server is fully functional, properly configured, and documented in the asset inventory.




