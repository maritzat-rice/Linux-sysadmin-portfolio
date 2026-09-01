# Install PHP on Web Server

## Objective
Enhance web server management skills by installing PHP and required extensions on a
Linux-based web server hosted in a vSphere environment.

---

## Task Summary
Install PHP on the staging web server as requested by the web development team.
Validate Apache functionality, enable the correct PHP module stream, install required
PHP packages, test PHP processing, and remove temporary test files as a security best
practice.

---

## Requirements
- VM: stage-web server
- PHP installation
- Apache validation
- PHP module stream configuration
- Test page creation and verification
- Removal of test file

*(All sensitive IPs, hostnames, and organization names have been redacted.)*

---

## Steps Performed

### 1. Access the Server

- SSH’d into the staging web server from the bastion host as root.

<img src="https://github.com/user-attachments/assets/b7d2b70a-2807-4356-be3f-c722826cb25b" width="175"/>

### 2. Verify Apache Service

**Checked that Apache was installed and running:**

- systemctl status httpd

<img src="https://github.com/user-attachments/assets/48ed1260-181e-423a-a329-2f955a508cfa" width="250"/>

**Apache service was active.**

---

### 3. Review PHP Module Streams

**Listed available PHP module streams:**

- dnf module list php

<img src="https://github.com/user-attachments/assets/9129c7ab-b76a-4106-8a30-ce89e7600e30" width="250"/>

---

### 4. Enable PHP 8.1 Module

**Enabled the correct PHP module stream:**

- dnf module enable php:8.1 -y

<img src="https://github.com/user-attachments/assets/ffe55896-c48b-4564-b2b4-a0c0a043f6df" width="300"/>

---

### 5. Install PHP + Extensions

**Installed PHP and commonly required extensions:**

- dnf install php php-cli php-common php-fpm php-mysqlnd php-opcache php-gd php-xml -y

<p>
<img src="https://github.com/user-attachments/assets/44a9896c-5943-4afb-a2ca-8405daadccb2" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/91eeb204-37bf-4d1b-a2e2-8f050c6b5298" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/280aaebf-7a2e-46ed-b713-af256f41bce1" width="300"/>
<p>

**Additional extensions installed:**

- php-mbstring
- php-pdo

---

### 6. Restart Apache

**Reloaded Apache to apply PHP module changes:**

- systemctl restart httpd

<img src="https://github.com/user-attachments/assets/0f460b2b-760f-40c0-9460-c00544438c63" width="200"/>

---

### 7. Verify PHP Installation

**Checked PHP version:**

- php -v

<img src="https://github.com/user-attachments/assets/eee98856-6e96-4691-9d50-8ab473726532" width="250"/>

PHP 8.1 successfully installed.

---

### 8. Create PHP Test Page

**Created a temporary PHP info file:**

- echo “<?php phpinfo(); ?>” >  /var/www/html/info.php 

<img src="https://github.com/user-attachments/assets/6ce9dc93-12c1-4cb1-b3af-ebff5f12b033" width="300"/>

- Ran ls -l /var/www/html/info.php

<img src="https://github.com/user-attachments/assets/98374139-1261-404f-98c2-d28ee9a5ef61" width="250"/>

**Opened the test page in a browser:**

- http://10.X.XX.176/info.php

**PHP info page displayed successfully.**

<p>
<img src="https://github.com/user-attachments/assets/bbfd1fb3-981d-458b-be9a-b3a608ef52a9" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/2096df34-e8ba-4271-a829-e3df68bd8560" width="300"/>
<p>

---

### 9. Remove Test File

**Removed the test file as a security best practice:**

- rm -f /var/www/html/info.php

<img src="https://github.com/user-attachments/assets/900e4782-ad6d-4358-bc45-5e3a6031db65" width="250"/>

---

## Challenges Encountered

Initially, the browser displayed a blank page due to cached content from an earlier
incorrect filename.
Verified PHP execution using `curl` on the server, then reopened the URL in a fresh
browser tab.
Issue resolved.

---

## Verification

- PHP 8.1 confirmed via CLI (`php -v`)
- PHP info page successfully rendered in browser
- Apache service running normally
- PHP modules loaded correctly

---

## Summary of Work Completed

- Verified Apache service
- Reviewed PHP module streams
- Enabled PHP 8.1
- Installed PHP and required extensions
- Restarted Apache to load modules
- Created and tested PHP info page
- Removed test file for security
- Confirmed PHP functionality through CLI and browser

**PHP installation completed successfully.**
