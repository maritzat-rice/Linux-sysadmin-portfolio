## Deploy WordPress Using Docker Containers

## Objective
Deploy a fully containerized WordPress website on **dev-app-mr1.XX.prod1** using Docker and MySQL. This task demonstrates container networking, multi‑container orchestration, troubleshooting, and application deployment.

## Summary
Installed Docker from the correct EL9 repository, created a Docker network, deployed MySQL and WordPress containers, verified container health, and confirmed the WordPress site is live at:

**http://10.X.XX.172:8080**

---

## Completed Tasks

### 🔹 1. Connected to dev-app Server

**From bastion:**

- ssh mrice@10.X.XX.172 
- sudo -i 
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/bca05778-977b-42d1-8b5d-e662bfc73275" width="250"/>

---

# 🟦 Docker Installation & Fix

### 🔹 2. Attempted Docker Install (Incorrect Repo)

- yum install -y docker

<p>
<img src="https://github.com/user-attachments/assets/6701eb50-661f-4a57-9792-ecd7ce69e808" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/9ccc8bc6-db61-418b-83f7-47c18cdc233a" width="275"/>
<p>

**Issue:**
- Server attempted to install **CentOS 7 Docker** from `Procore_Centos7_Extras_x86_64`
- Incompatible with EL9 → installation blocked

### 🔹 3. Removed Old Docker Metadata

- yum remove -y docker docker-client docker-client-latest docker-common docker-latest \ docker-latest-logrotate docker-logrotate docker-engine

<p>
<img src="https://github.com/user-attachments/assets/d3662a47-6311-42de-a4d7-37570927a41a" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/f7f7eb6e-7dc2-4eeb-ae53-0696e8f585d2" width="250"/>
<p>


### 🔹 4. Installed Required Tools

- yum install -y yum-utils

<p>
<img src="https://github.com/user-attachments/assets/42757c54-0d9f-49a2-b805-da5905e07bdd" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/eb615c0b-c796-4eb0-96be-79a77e7c6c6b" width="250"/>
<p>


### 🔹 5. Added Official Docker Repo

- yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

<p>
<img src="https://github.com/user-attachments/assets/88cf4d71-5945-4ebc-9202-ec24c8fd27ee" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/79784105-d1ac-4126-b6fb-582299ccd2b8" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/5a8c3870-ba09-4eee-905b-e4fd83f25e77" width="250"/>
<p>


### 🔹 6. Installed & Enabled Docker

- systemctl enable --now docker

<img src="https://github.com/user-attachments/assets/049ec7f9-a765-44aa-b889-92878c209d1e" width="275"/>

**Docker is now running correctly.**

---

# 🟦 Docker Network & Containers

## Create Docker Network

- docker network create wpnet

<img src="https://github.com/user-attachments/assets/9065c053-7a8c-4ca1-b56c-5b2066216003" width="250"/>

---

## Deploy MySQL Container

- docker run -d \ 
- --name wpdb \ 
- --network wpnet \
- -e MYSQL_ROOT_PASSWORD=pass123 \ 
- -e MYSQL_DATABASE=wpdb \ 
- -e MYSQL_USER=wpuser \ 
- -e MYSQL_PASSWORD=wppass \ 
- mysql:8.0

<img src="https://github.com/user-attachments/assets/db6b23b1-7883-448e-a080-a5818e9867bc" width="250"/>

**Verified:**

- docker ps

<img src="https://github.com/user-attachments/assets/210f5e2f-263e-49dd-949f-4cc31fe356b8" width="350"/>

MySQL container running.

---

## Deploy WordPress Container

- docker run -d \ 
- --name wordpress \ --network wpnet \ 
- -p 8080:80 \ -e WORDPRESS_DB_HOST=wpdb \ 
- -e WORDPRESS_DB_USER=wpuser \ 
- -e WORDPRESS_DB_PASSWORD=wppass \ 
- -e WORDPRESS_DB_NAME=wpdb \ 
- Wordpress

<p>
<img src="https://github.com/user-attachments/assets/ddde47de-8d2d-4f90-9819-8a88fafc1927" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/b5bcf3d6-7587-4b87-8aea-5145de6694a2" width="250"/>
<p>

**Verified:**

- docker ps

<img src="https://github.com/user-attachments/assets/8b72ce74-8f34-43cc-bca4-6d61f0b76673" width="350"/>

**Both containers running successfully.**

---

# 🟦 WordPress Verification

### 🔹 7. Accessed WordPress Site

**Opened browser:**

- http://10.X.XX.172:8080

**Result:**
- WordPress installation page loads  
- Database connection successful  
- Containers communicating over `wpnet`  
- Deployment complete  

---

## Result
Successfully deployed a fully containerized WordPress environment on **dev-app-mr1.XX.prod1** using Docker.  
MySQL and WordPress containers are running, networked, and serving the site at:

**http://10.X.XX.172:8080**

This ticket demonstrates real‑world container orchestration, troubleshooting, and application deployment.

