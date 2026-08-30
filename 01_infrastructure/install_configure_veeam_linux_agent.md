## Install & Configure Veeam Standalone Linux Agent (Full System Backup)

## Objective
Deploy a centralized backup solution using the Veeam Agent for Linux. Configure full system backups for **dev-app-mr1.XX.prod1** and **stage-web-mr1.XX.prod1**, storing backup data on an NFS repository hosted on **dev-performance-mr1.XX.prod1**. Validate restore functionality and confirm service integrity post‑restore.

## Summary
Set up an NFS backup repository on **dev-performance**.  
Installed Veeam Agent on **dev-app** and **stage-web**, configured full machine backup jobs, resolved firewall issues, and successfully mounted a restore point.  
Verified that critical services (HTTPD and NFS) remained stable after restore testing.

---

# 🟦 Part 1 — Configure NFS Backup Repository (dev-performance-mr1.XX.prod1)

### 🔹 1. Installed NFS Server Packages
- sudo -i 
- dnf install -y nfs-utils

<p>
<img src="https://github.com/user-attachments/assets/f3b70259-74b7-4677-8547-86f519e1f67a" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/53227323-7516-4360-8b20-76f39a744bd8" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d56b0606-b7ff-407d-8e9b-faf1d16601f6" width="250"/>
<p>

### 🔹 2. Created Backup Directory
- mkdir -p /Veeam_Backup 
- chmod 777 /Veeam_Backup

<img src="https://github.com/user-attachments/assets/ff34212e-8a0a-4f49-9945-fe30a1658578" width="250"/>

### 🔹 3. Configured NFS Export
- vi /etc/exports 
- /Veeam_Backup 10.X.XX.0/24(rw,sync,no_root_squash)

<p>
<img src="https://github.com/user-attachments/assets/169979e9-ebfa-468b-a9f0-2c1179a666f6" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/a51718df-bada-437b-9490-bed0321c9fd6" width="250"/>
<p>

### 🔹 4. Enabled & Started NFS Services
- systemctl enable --now nfs-server 
- exportfs -rav 
- exportfs -v

<p>
<img src="https://github.com/user-attachments/assets/dae761b1-0107-4db5-b31b-56f5bb699e8a" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ebefdbaf-d85f-4447-8503-c8de04dfd825" width="250"/>
<p>

---

# 🟦 Part 2 — Install & Configure Veeam Agent (dev-app-mr1.XX.prod1)

### 🔹 5. Added Veeam Repository

- sudo vi /etc/yum.repos.d/veeam.repo

**[veeam]**

name=Veeam for Linux 

baseurl=https://repository.veeam.com/backup/linux/agent/rpm/el/9/x86_64/ 

enabled=1 

gpgcheck=1 

gpgkey=https://repository.veeam.com/keys/veeam.gpg


<img src="https://github.com/user-attachments/assets/6227bbaa-a637-4c11-8a35-1c8fe77e9283" width="250"/>

### 🔹 6. Installed Required Packages

- sudo dnf remove veeam -y 
- sudo dnf install -y blksnap 
- sudo dnf install -y veeam

<p>
<img src="https://github.com/user-attachments/assets/b926d01e-1eb1-4dad-9528-e08141c5a1e0" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/6adc07f2-239d-49f0-a039-d449917df711" width="250"/>
<p>

### 🔹 7. Verified Installation

- sudo veeamconfig version

<img src="https://github.com/user-attachments/assets/061c1984-1070-4e03-a93f-64356de6fd1c" width="250"/>

### 🔹 8. Configured Backup Job (TUI)

**sudo veeam**

**Selections:**
- **C** (Configure)
- Job Name: `dev-app-test-backup`
- Backup Type: **Entire Machine**
- Repository: **Shared Folder → NFS**
- NFS Server: `10.1.XX.XX75`
- Folder: `/Veeam_Backup`
- Schedule: Daily @ 00:30
- Start Job Now → Finish

<p>
<img src="https://github.com/user-attachments/assets/cd19cb31-acc5-4618-a4f7-e642d064f65c" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/273aff32-cb66-4ddd-91ba-27af5c3cf791" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/f50cdd36-31b7-4935-9924-763b821d4d13" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d0a4d123-b630-412f-b945-9d642c3d961b" width="250"/>
<p>

### 🔹 Fixed NFS Connectivity Issue
**On dev-app:**

**Selections:**
- **C** (Configure)
- Job Name: `dev-app-test-backup`
- Backup Type: **Entire Machine**
- Repository: **Shared Folder → NFS**
- NFS Server: `10.X.XX.175`
- Folder: `/Veeam_Backup`
- Schedule: Daily @ 00:30
- Start Job Now → Finish

<p>
<img src="https://github.com/user-attachments/assets/e4850920-31b6-4f65-8302-84e446bbaddb" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d001a1f8-4c33-47d2-8030-aa70e6eab4d6" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ff80c585-3009-4e9d-b341-1956c5aac771" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/437b0925-b772-41f8-81f3-d84c8bd0b90a" width="250"/>
<p>

### 🔹 9. Fixed NFS Connectivity Issue

**On dev-performance:** error that there is no connection to hosts. 

Found NFS, RPC and mountd were missing on firewalld.

- firewall-cmd --add-service=nfs --permanent

<img src="https://github.com/user-attachments/assets/a8b48918-29fd-4aaf-a5cb-62c96923931a" width="250"/>

- firewall-cmd --add-service=rpc-bind --permanent

<img src="https://github.com/user-attachments/assets/71525e31-1e0a-4c20-8444-9f4cfa8ed7fd" width="250"/>

- firewall-cmd --add-service=mountd --permanent

<img src="https://github.com/user-attachments/assets/324f8684-4780-463a-a5b9-d0394f00775e" width="250"/>

- firewall-cmd --reload

<img src="https://github.com/user-attachments/assets/62ed684b-ff8e-4ddd-bf0d-ea9e5d9ec603" width="250"/>

- showmount -e 10.X.XX.175

<p>
<img src="https://github.com/user-attachments/assets/69d6b735-d32a-490a-ba42-cdbb86f7d178" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ea9e8c50-abf4-4592-b2eb-3b764991ec26" width="500"/>
<p>

# 🟦 Part 3 — Install & Configure Veeam Agent (stage-web-mr1.XX.prod1)

### 🔹 10. Installed Prerequisites

- sudo dnf install -y nfs-utils

<img src="https://github.com/user-attachments/assets/8a927555-d1d0-48b6-98d4-22a1a2e900d0" width="250"/>

### 🔹 11. Added Veeam Repo

- sudo vi /etc/yum.repos.d/veeam.repo

**[veeam]**

name=Veeam Backup for GNU/Linux – $basearch 

baseurl=https://repository.veeam.com/backup/linux/agent/rpm/el/9/$basearch 

enabled=1 

gpgcheck=1 

gpgkey=https://repository.veeam.com/keys/RPM-E6FBD664


### 🔹 12. Installed Veeam

- sudo dnf install -y epel-release 
- sudo dnf install -y veeam 
- sudo veeamconfig version


### 🔹 13. Launched Veeam TUI

- sudo veeam

Configured backup job similarly to dev-app.

---

# 🟦 Part 4 — Restore Test (stage-web-mr1.XX.prod1)

### 🔹 14. Mounted Restore Point

Inside Veeam TUI:
- Selected **Restore**
- Mounted restore point to `/mnt/backup`

Verified:
- ls /mnt/backup


**Confirmed full filesystem restored in read‑only mode.**

---

# 🟦 Part 5 — Instructor Follow‑Up: Service Status After Restore

### 🔹 HTTPD (Apache)

- Restore was read‑only → no changes to live system.

**Checked:**
- systemctl status httpd


**Result:**
- Service remained active and running normally.

### 🔹 NFS (Client)
Stage-web is an NFS client, not the server.

**Checked:**
- systemctl status nfs-utils 
- mount | grep nfs


**Outcome:**
- NFS mounts remained active and unchanged  
- No configuration modified  
- nfs-utils.service inactive (expected for client systems)

---

## Result
Successfully deployed Veeam Agent on **dev-app** and **stage-web**, configured full system backups, and validated restore functionality.  
NFS repository on **dev-performance** is fully operational.  
Critical services remained stable after restore testing.

*This ticket demonstrates advanced backup engineering, disaster recovery readiness, and multi‑server coordination in an enterprise Linux environment.*

