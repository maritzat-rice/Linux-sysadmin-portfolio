## Configure FTP Server & Client (File Transfer Between dev-app and stage-web)

## Objective
Configure an FTP server on **dev-app-mr1.XX.prod1** and an FTP client on **stage-web-mr1.XX.prod1**, then successfully transfer a file between the two systems. This task demonstrates practical networking, SELinux tuning, firewall configuration, and FTP troubleshooting.

## Summary
Installed and configured vsftpd on dev-app, enabled FTP firewall rules, adjusted SELinux for home‑directory access, installed FTP client on stage-web, connected successfully, downloaded the required file, and verified the transfer.

---

## Completed Tasks

### 🔹 1. Connected to dev-app Server

**From bastion:**

- ssh mrice@10.X.XX.172

**Verified:**
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/21232528-aaa5-430e-9858-fa620ee627f1" width="150"/>

---

# 🟦 FTP Server Setup (dev-app)

### 🔹 2. Copied Required File to Home Directory

- cp /nfs/incoming/vhosts/ftp-files/ftp-prod.config ~/ 
- ls -l ~/ftp-prod.config

<p>
<img src="https://github.com/user-attachments/assets/3a0f47fe-cd33-451c-89ad-dbe79c250308" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/fcb96f87-0b8e-4502-b6ec-5359edce14be" width="250"/>
<p>

**File confirmed.**

---

### 🔹 3. Installed FTP Server (vsftpd)

- sudo dnf install vsftpd -y 

<img src="https://github.com/user-attachments/assets/61b48d75-1253-4674-ab3a-7f891a4d08cd" width="250"/>

- sudo systemctl enable --now vsftpd 
- systemctl status vsftpd

<p>
<img src="https://github.com/user-attachments/assets/34b46ae4-c04a-4093-b0f9-7fb8009247d1" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/41b839c7-958f-49b2-ae02-7f9906f67fb4" width="250"/>
<p>

**vsftpd running successfully.**

---

### 🔹 4. Opened FTP in Firewall

- sudo firewall-cmd --add-service=ftp --permanent 
- sudo firewall-cmd --reload

<img src="https://github.com/user-attachments/assets/3658f728-23ac-4773-a2ed-f1e33f74601d" width="250"/>

---

### 🔹 5. Adjusted SELinux for FTP Access

- sudo setsebool -P ftpd_full_access on

<img src="https://github.com/user-attachments/assets/2c943289-c7af-481d-8ac4-293e6e9843c8" width="250"/>

*This allows vsftpd to read files in user home directories — required for successful transfers.*

---

# 🟦 FTP Client Setup (stage-web)

### 🔹 6. Logged Into stage-web

- ssh mrice@10.X.XX.176 
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/7d863dc3-31e2-4ab4-a2d9-d5a64241ded0" width="150"/>

---

### 🔹 7. Installed FTP Client

- sudo dnf install ftp -y

<img src="https://github.com/user-attachments/assets/6545a866-89fc-497e-b16b-7304fae7f48d" width="250"/>

---

# 🟦 File Transfer Test

### 🔹 8. Connected to FTP Server

**DNS resolution note:**
- `.prod1` hostname failed  
- Connected using correct hostname: **dev-app-mr1.procore.dev**

- ftp dev-app-mr1.XXX.dev

<img src="https://github.com/user-attachments/assets/9067e68d-b13d-4847-8db2-2d1ee7d7f654" width="175"/>

---

### 🔹 9. Downloaded File

- get ftp-prod.config 
- bye

<img src="https://github.com/user-attachments/assets/7a4c01fe-c9f1-45aa-a296-25df678cfb6c" width="250"/>

**Verified on stage-web:**

- ls -l ftp-prod.config

<img src="https://github.com/user-attachments/assets/80d856cf-b6b7-4293-bb25-e129f13db133" width="250"/>

**Output:**

- -rw-r--r--. 1 mrice mrice ... ftp-prod.config


*File successfully transferred.*

---

## Result

**Successfully configured:**
- **FTP server** on dev-app  
- **FTP client** on stage-web  
- **Firewall + SELinux** for FTP  
- **File transfer** of `ftp-prod.config`  

**This demonstrates practical networking, service configuration, and troubleshooting across multiple Linux systems.**



