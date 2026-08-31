## Install & Configure Apache Web Server on stage-web

## Objective
Deploy and configure the Apache web server on **stage-web-mr1.XX.prod1**, ensuring the service is installed, started, enabled, and accessible through the firewall. This task demonstrates foundational web‑services administration skills.

## Summary
Installed Apache (httpd), enabled and started the service, configured firewall rules to allow HTTP traffic, and verified functionality using curl. Apache is now fully operational on the staging web server.

---

## Completed Tasks

### 🔹 1. Connected to Stage-Web Server

**From bastion:**
- ssh mrice@10.X.XX.176 

<img src="https://github.com/user-attachments/assets/1503e206-10e5-4316-a881-c105aba1123e" width="250"/>

- sudo -i

<img src="https://github.com/user-attachments/assets/3b2ba762-1203-4b0d-b296-50ac4adc0e75" width="175"/>

---

## Apache Installation & Configuration

### 🔹 2. Installed Apache Web Server

- dnf install httpd -y

<img src="https://github.com/user-attachments/assets/dc0ac5e2-f402-41a6-a773-5228a6a57855" width="350"/>

### 🔹 3. Enabled & Started Apache

- systemctl enable httpd 
- systemctl start httpd 
- systemctl status httpd

<p>
<img src="https://github.com/user-attachments/assets/0aa3e284-3d51-4fa9-8265-d135a19d817e" width="350"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/e81821d7-4393-4194-93b5-4e265857fc8c" width="350"/>
<p>

**Apache service is active and running.**

---

## Firewall Configuration

### 🔹 4. Allowed HTTP Traffic

- firewall-cmd --permanent --add-service=http 

<img src="https://github.com/user-attachments/assets/27ff6724-8017-417c-bad0-c4fb980f93a7" width="250"/>

- firewall-cmd –reload

<img src="https://github.com/user-attachments/assets/682eb75b-9820-4a56-96e9-d0dedd1cbfd3" width="200"/>

**Verified:**
- firewall-cmd --list-all

<img src="https://github.com/user-attachments/assets/837571e9-f610-4e01-8185-8d93da653b98" width="300"/>

HTTP service is now allowed through the firewall.

---

## Functional Test

### 🔹 5. Tested Apache Locally

- curl localhost

**Received default Apache test page output, confirming successful installation and service availability.**

---

## Result
Apache (httpd) is fully installed, enabled, and running on **stage-web-mr1.XX.prod1**.  
Firewall rules allow HTTP traffic, and the service responds correctly to local requests.  
This completes the required web‑services deployment task.




