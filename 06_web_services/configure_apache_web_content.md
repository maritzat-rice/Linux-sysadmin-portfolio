## Configure Apache Web Content (Ariclaw Website Deployment)

## Objective
Deploy the Ariclaw website content from GitLab onto the **stage-web-mr1.XX.prod1** server.  
This task demonstrates practical web‑services administration including GitLab SSH access, repository cloning, Apache content deployment, and permissions tuning.

## Summary
Verified SSH access to GitLab, cloned the Ariclaw repository, cleared the default Apache web root, deployed the site content, corrected permissions, restarted Apache, and confirmed the site is live at **http://10.X.XX.176**.

---

## Completed Tasks

### 🔹 1. Connected to Stage-Web Server

**From bastion:**

- ssh mrice@10.X.XX.176 
- sudo -i

<img src="https://github.com/user-attachments/assets/85a8288a-ea65-46f5-921a-9516e8b0fea0" width="200"/>

---

## GitLab Access & Repository Deployment

### 🔹 2. Verified SSH Access to GitLab

- ssh -T git@gitlab.com

**Expected output:**

Welcome to GitLab, @maritzat.rice!

<img src="https://github.com/user-attachments/assets/a8215859-02a5-4a1f-a9a6-449a0ade9666" width="250"/>

### 🔹 3. Installed Git

- sudo dnf install git -y 

<p>
<img src="https://github.com/user-attachments/assets/c3bb0fd0-4de8-4ff8-bd9a-e18c9925af85" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/dc14c65c-bc3a-458b-b1c1-24f12ab81e5e" width="300"/>
<p>

- git –version

<img src="https://github.com/user-attachments/assets/521d8bbf-cb46-4053-b6b4-4a536e340b4e" width="200"/>

### 🔹 4. Cloned Ariclaw Repository

- cd ~ 
- git clone git@gitlab.com:XXXXXX/ariclaw.git 

<img src="https://github.com/user-attachments/assets/b766460c-63ac-41c0-a010-582972b767f2" width="250"/>

- cd ~/ariclaw 
- ls -l

<img src="https://github.com/user-attachments/assets/c8a14f48-cc45-42c0-b06d-8dfcf26036e2" width="250"/>

**Repository cloned successfully.**

---

## Apache Web Content Deployment

### 🔹 5. Cleared Default Apache Web Root

- sudo rm -rf /var/www/html/*

<img src="https://github.com/user-attachments/assets/4ff47023-c65e-4d3a-b40c-218209002d0e" width="250"/>

### 🔹 6. Copied Ariclaw Site Into Web Root

- sudo cp -r ~/ariclaw/* /var/www/html/

<img src="https://github.com/user-attachments/assets/8622ba80-31b3-4ad9-bc02-dbd1e2ea3900" width="250"/>

### 🔹 7. Fixed Permissions

- sudo chown -R apache:apache /var/www/html/

<img src="https://github.com/user-attachments/assets/df4f21cf-8734-44bd-b55d-fac747f12c20" width="270"/>

### 🔹 8. Restarted Apache

- systemctl restart httpd 
- systemctl status httpd

<img src="https://github.com/user-attachments/assets/5514338d-e664-48e0-b9cf-266848380ece" width="250"/>

**Apache is active and running.**

---

## Functional Verification

### 🔹 9. Tested Website

**Opened browser:**

- http://10.X.XX.176

<img src="https://github.com/user-attachments/assets/cc831941-e8a3-410f-9add-38ed52d5dad6" width="250"/>

Result:
- Ariclaw website loads successfully  
- Content is served from **stage-web-mr1.XX.prod1**  
- Deployment verified and complete  

---

## Result
The Ariclaw website was successfully deployed to **stage-web-mr1.XX.prod1** using GitLab SSH access and Apache web‑root configuration.  
Apache is running, permissions are correct, and the site is fully accessible at **http://10.X.XX.176**.






