## Install LAMP Stack & Deploy CRM Application

## Objective
Deploy a full LAMP stack (Apache, PHP, MariaDB, phpMyAdmin) on **stage-web-mr1.XX.prod1** and configure the Small CRM Project using PHP and MySQL. This task demonstrates full‑stack web deployment, database configuration, PHP module management, and application troubleshooting.

## Summary
Installed Apache, PHP, MariaDB, phpMyAdmin, configured firewall rules, deployed CRM application files, created the CRM database, imported SQL schema, updated PHP database connection files, and validated both admin and user functionality.

---

## Completed Tasks

### 🔹 1. Verified Base System State

- hostname 
- whoami 

<img src="https://github.com/user-attachments/assets/2a9b9f2b-dc0a-40b9-8834-ec052750cfe0" width="175"/>

- ip a

<img src="https://github.com/user-attachments/assets/706ac8e5-ea2c-4ed0-a60e-b50bdbdac916" width="350"/>

---

# 🟦 LAMP Stack Installation

## Apache & MariaDB

### 🔹 2. Installed EPEL

- yum install epel-release -y

<img src="https://github.com/user-attachments/assets/dea29e3d-664b-4c48-ae7b-c54895d911d9" width="250"/>

### 🔹 3. Installed MariaDB Server

- sudo yum install mariadb-server -y 
- sudo systemctl enable --now mariadb 

<p>
<img src="https://github.com/user-attachments/assets/c1148509-cf31-420c-8ca5-c18209fb2b0e" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ebabb9b0-34cf-4631-b153-bbf80467635f" width="300"/>
<p>

- sudo mysql_secure_installation 
- systemctl status mariadb

<p>
<img src="https://github.com/user-attachments/assets/6843c624-c8b5-48d6-a011-ce3019019270" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/be42caf1-eab2-43d3-97af-fc820f8023ab" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/48ecda03-6670-428c-b2f1-2ba8444bcf7b" width="300"/>
<p>


### 🔹 4. Opened Firewall Ports

- firewall-cmd --permanent --add-service=http 
- firewall-cmd --permanent --add-service=https 
- firewall-cmd –reload

<img src="https://github.com/user-attachments/assets/272ca893-4dad-440e-a3e3-cb1dc3882b9c" width="250"/>

---

## PHP Installation & Configuration

### 🔹 5. Installed PHP & Core Modules

- sudo yum -y install yum-utils 
- sudo yum update -y 
- sudo yum -y install php php-opcache

<p>
<img src="https://github.com/user-attachments/assets/0032db12-982a-437b-b9f3-9b9ea9f68576" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/e7939f68-62d6-4d0b-ab87-b1e749c5feac" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/b0ea74a7-bfc3-454b-b41c-a95a92673ccd" width="250"/>
<p>

### 🔹 6. Verified PHP

- Created `/var/www/html/info.php`:

<img src="https://github.com/user-attachments/assets/a49e4746-de77-4380-924c-1c9354d1dcdd" width="250"/>

Added the following content to the file:

<?php phpinfo(); ?>

<img src="https://github.com/user-attachments/assets/b13ebf8d-98da-489d-a45b-c2448d737357" width="125"/>


**Tested:**

http://10.X.XX.176/info.php

<img src="https://github.com/user-attachments/assets/9c7e3108-00ee-46e5-92ce-e88b55526358" width="300"/>

- php -v

<img src="https://github.com/user-attachments/assets/d59f2ee8-d707-467b-83fb-f5708f6ad8d9" width="250"/>


### 🔹 7. Installed MySQL & Common PHP Modules

- sudo yum -y install php-mysqlnd php-pdo 

<img src="https://github.com/user-attachments/assets/5616de07-f7ff-44d8-9782-06ca74720c8f" width="250"/>

- sudo yum -y install php-gd php-ldap php-odbc php-pear php-xml php-xmlrpc php-mbstring php-soap curl curl-devel

<img src="https://github.com/user-attachments/assets/b8a52bcd-7361-4733-81e3-9df56cc1bf33" width="300"/>

- sudo systemctl restart httpd

<img src="https://github.com/user-attachments/assets/9b2c5e1b-0105-4af6-b662-a717de72c2a1" width="250"/>

Verified via `info.php`.
- http://10.1.30.176/info.php

<p>
<img src="https://github.com/user-attachments/assets/05ab02e0-5e18-482b-8617-de36b191ed69" width="350"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d64dc21d-685e-447f-b855-4ae02cb183df" width="350"/>
<p>

---

## phpMyAdmin Installation

### 🔹 8. Installed phpMyAdmin

- yum install phpmyadmin -y

<p>
<img src="https://github.com/user-attachments/assets/76777cbd-9369-4351-b3d7-ad747d590580" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d9fec83c-c8e0-49dc-9a4e-ede9ca6f3ea0" width="300"/>
<p>

**Edited config:**

- vi /etc/httpd/conf.d/phpMyAdmin.conf

<img src="https://github.com/user-attachments/assets/d2238e73-eb52-4df0-9afc-1813f5f40259" width="250"/>


**Changed:**

- Require local → Require all granted

<img src="https://github.com/user-attachments/assets/5859a495-e40f-44a0-91e0-ce7f6261ba32" width="175"/>

**Restarted Apache:**

- systemctl restart httpd

<img src="https://github.com/user-attachments/assets/b22c6917-673a-41bf-84ec-14a9a88d9246" width="250"/>

**Accessed:**

- http://10.X.XX.176/phpmyadmin


**Logged in successfully.**

<p>
<img src="https://github.com/user-attachments/assets/3fd5f924-53b0-480f-b1fb-eafc151912ed" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/b9cf05cd-5e9e-4c6c-80d5-e10d3263f25f" width="250"/>
<p>

---

# 🟦 CRM Application Deployment

## Download & Extract CRM Project

<img src="https://github.com/user-attachments/assets/cae924fd-f881-4f95-b7b2-0b737c698061" width="250"/>


### 🔹 9. Downloaded CRM ZIP

-	cd /tmp 
-	wget https://gitlab.com/procoreplusmd/crm-project/-/archive/main/crm-project-main.zip?ref_type=heads 

<img src="https://github.com/user-attachments/assets/4b7ed40e-57ce-4ba3-af63-5526d9842d4a" width="250"/>

- unzip 'crm-project-main.zip?ref_type=heads'

<img src="https://github.com/user-attachments/assets/7498bcc6-ae32-4832-9e0e-cf8d77f575ca" width="250"/>


### 🔹 10. Copied CRM Application to Apache Web Root

- cp -r /tmp/crm-project-main /var/www/html/crm 
- ls /var/www/html

<p>
<img src="https://github.com/user-attachments/assets/9b17efef-4fcf-47b3-b4ee-8ec2df3b21fb" width="350"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/cdb023fb-ab7e-4ffd-99c6-3d1be7d14d98" width="350"/>
<p>

**CRM folder confirmed.**

---

## Database Setup

### 🔹 11. Created CRM Database

- mysql -u root -p 
- CREATE DATABASE crm; 
- EXIT;

<p>
<img src="https://github.com/user-attachments/assets/d77ae304-dffa-4ee4-a7a6-dd6a873df9f6" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/a64d7aea-172d-4fae-a4d2-e3a5897d405c" width="175"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/a20ef80c-1ad1-4334-88b9-b50780b997a0" width="125"/>
<p>


### 🔹 12. Located SQL File

- find /var/www/html/crm -name "*.sql"

<img src="https://github.com/user-attachments/assets/9798a284-bf6a-4e2c-ab2e-c1547efbe06c" width="350"/>


### 🔹 13. Imported SQL Schema

- mysql -u root -p crm < "/var/www/html/crm/Small CRM Projects Using PHP and MySQL 2/SQL File/crm.sql"

<img src="https://github.com/user-attachments/assets/0146dab2-5909-44b1-990e-c631a9a642d1" width="350"/>

---

## Update Database Connection Files

### 🔹 14. Edited dbconnection.php Files

**Main file:**

- vi /var/www/html/crm/dbconnection.php

<img src="https://github.com/user-attachments/assets/ee6c48d4-128d-494f-9ef4-007a824e9f08" width="250"/>

**Admin file:**

- vi /var/www/html/crm/admin/dbconnection.php

<img src="https://github.com/user-attachments/assets/ea3e8fa0-9cfe-4af0-95f1-5e8626e1a0a3" width="250"/>

**Updated:**

- $con=mysqli_connect("localhost", "root", "PasswordUsed", "crm");

<img src="https://github.com/user-attachments/assets/9c53a6fb-f1ad-458c-9337-430db0f513b2" width="200"/>

---

# 🟦 CRM Application Testing

## Admin Panel

**Accessed:**

- http://10.X.XX.176/crm/admin

<p>
<img src="https://github.com/user-attachments/assets/ddda6474-f9f8-4e45-9c4d-3aa67b023983" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/9d2e5538-eed0-45a1-87a1-b7bb6fbabd85" width="250"/>
<p>

**Credentials for the Admin panel loaded successfully.**

---

## Frontend User Panel

**Accessed:**

- http://10.X.XX.176/crm


- Created a new user via **Sign Up**.

**Logged in using:**
- Username: *email used during signup*
- Password: **Test@XXXX#**

<img src="https://github.com/user-attachments/assets/8cffa1bd-15cb-4857-b605-9ae782742c26" width="250"/>

**User panel loaded successfully.**

---

## Result
The full LAMP stack was successfully deployed on **stage-web-mr1.XX.prod1**.  
CRM application installed, database configured, SQL imported, connection files updated, and both admin and user interfaces verified.

This ticket demonstrates full‑stack deployment, database administration, PHP configuration, and application troubleshooting in a production‑like environment.
