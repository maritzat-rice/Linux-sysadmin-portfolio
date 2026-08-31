## Apache Version Check on stage-web

## Objective
Provide the Apache version running on **stage-web-mr1.XX.prod1** to assist the development team with troubleshooting. This task demonstrates basic web‑services administration and service validation.

## Summary
Connected to the staging web server, elevated privileges, and retrieved the Apache version using the `httpd -v` command. Confirmed the server is running **Apache/2.4.62 (CentOS Stream)**.

---

## Completed Tasks

### 🔹 1. Connected to Stage-Web Server

**From bastion:**

- ssh mrice@10.X.XX.176

<img src="https://github.com/user-attachments/assets/0c14b749-edd2-42c3-bcb0-43b00868808c" width="200"/>

**Verified:**

- hostname 
- whoami


### 🔹 2. Elevated to Root

- sudo -i 
- whoami

<img src="https://github.com/user-attachments/assets/b5c4583e-5e09-477e-aadd-f334b3c18afc" width="155"/>

---

## Apache Version Retrieval

### 🔹 3. Checked Apache Version

- httpd -v

<img src="https://github.com/user-attachments/assets/037f1ee5-2bbc-41ca-9ef3-dca5b67a4f49" width="175"/>

**Output:**

- Server version: Apache/2.4.62 (CentOS Stream)


**Apache is installed and functioning normally.**

---

## Result
The Apache version running on **stage-web-mr1.XX.prod1** is:

**Apache/2.4.62 (CentOS Stream)**

*This information has been provided to support the development team’s troubleshooting efforts.*


