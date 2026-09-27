## Configure NFS Server

---

## Objective
Configure an NFS server on **dev-app-mr1.XXX.prod1**, create a user-specific NFS export, download a test file into the share, and validate successful NFS mounting and access from the **stage-web** client server.

---

## Summary
Installed NFS server utilities, created a dedicated NFS export directory, configured `/etc/exports`, fixed hostname resolution, enabled required services, configured firewall rules, downloaded a test RPM file into the NFS share, and successfully mounted and verified the share from the stage-web client.

---

## Completed Tasks

### 1. Logged Into dev-app Server

- ssh mrice@bastion 

<img src="https://github.com/user-attachments/assets/0fa38a08-bb3f-4a1a-9ada-2b9fc12b34f1" width="200"/>

- ssh adminuser@dev-app-mr1.XXX.prod1

<img src="https://github.com/user-attachments/assets/19a9358c-6499-42be-b45b-9e41cf5dc204" width="250"/>

- sudo -i

<img src="https://github.com/user-attachments/assets/7afb2376-3dea-40ef-9412-caf4ed78771e" width="175"/>

- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/4e040cfe-2e48-4900-ad5a-a42248a1a348" width="175"/>

### Confirmed correct VM: **dev-app-mr1.XXX.prod1**

---

### 2. Installed NFS Server Packages

- dnf install -y nfs-utils

<p>
<img src="https://github.com/user-attachments/assets/d0f199eb-2025-4c92-a542-503df8404382" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/a430a5c6-3a2d-4fa2-bca6-d437ce7fa5a6" width="250"/>

<p>
<img src="https://github.com/user-attachments/assets/a3dbf3f8-ed09-4d9f-ae4f-05d53a925c83" width="250"/>
<p>

---

### 3. Created NFS Export Directory

- mkdir /nfs-mrice 

- chmod 755 /nfs-mrice

<img src="https://github.com/user-attachments/assets/5d789a8c-dcc3-4d7d-bcb4-07d965f5b5c5" width="200"/>

---

### 4. Configured /etc/exports

### Added NFS export entry:

- echo "/nfs-mrice stage-web-mr1.XXX.prod1(rw,sync,no_root_squash)" >> /etc/exports
- cat /etc/exports

<img src="https://github.com/user-attachments/assets/44f001d8-b414-457f-a53a-b764fe68a74f" width="300"/>

---

### 5. Enabled and Started NFS Services

- systemctl enable --now nfs-server 

- systemctl enable --now rpcbind 

- systemctl status nfs-server

<p>
<img src="https://github.com/user-attachments/assets/5c22bf8c-6cc0-4460-993c-9a4643512158" width="275"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/c56d6026-6d44-41c2-9008-3fa456481591" width="250"/>
<p>

---

### 6. Fixed Hostname Resolution for NFS

***The dev-app server could not resolve the stage-web hostname.***

### Added entry to `/etc/hosts`:

- echo "10.X.XX.176 stage-web-mr1.XXX.prod1" >> /etc/hosts

### Reloaded NFS exports:

- exportfs -rav

<img src="https://github.com/user-attachments/assets/e9709607-6c92-4525-9aff-020ff3cf87c9" width="250"/>

NFS export became fully active and resolvable.

---

### 7. Configured Firewall for NFS

- firewall-cmd --permanent --add-service=nfs 

- firewall-cmd --permanent --add-service=mountd 

- firewall-cmd --permanent --add-service=rpc-bind 

- firewall-cmd --reload 

<img src="https://github.com/user-attachments/assets/4cca5c19-cd72-44b8-8751-73c719929587" width="250"/>

- firewall-cmd --list-services

<img src="https://github.com/user-attachments/assets/94fd7e22-f79e-4f2f-8b05-39a6ad08a829" width="250"/>

***Firewall is now NFS-ready.***

---

### 8. Downloaded Test RPM File Into NFS Share

- cd /nfs-mrice 

curl -O https://download.java.net/java/GA/jdk18.0.1.1/65ae32619e2f40f3a9af3af1851d6e19/2/GPL/openjdk-18.0.1.1_linux-x64_bin.tar.gz

<img src="https://github.com/user-attachments/assets/d1c851af-415c-47a7-9d7a-5becc9c6afdd" width="300"/>

- ls -lh /nfs-mrice

<img src="https://github.com/user-attachments/assets/425f1a28-be29-4608-8711-959b1676287e" width="300"/>

### NFS server configuration is complete.

---

## NFS Client Configuration (stage-web)

### 9. Logged Into stage-web Server

- ssh root@stage-web-mr1.XXX.prod1 

- hostname 

- whoami

<img src="https://github.com/user-attachments/assets/bdccb91d-7722-49f7-b28a-57b5040498aa" width="150"/>

---

### 10. Installed NFS Client Utilities

- sudo dnf install -y nfs-utils

<img src="https://github.com/user-attachments/assets/26d1253f-0722-4c48-a51c-1fc634162849" width="250"/>

---

### 11. Created Mount Point

- sudo mkdir /mnt/nfs-mrice

<img src="https://github.com/user-attachments/assets/38bdb156-c37f-4270-89cd-48ec86243321" width="250"/>

---

### 12. Mounted the NFS Share

- sudo mount dev-app-mr1.XXX.dev:/nfs-mrice /mnt/nfs-mrice

<img src="https://github.com/user-attachments/assets/d9658900-41df-455c-91a0-4ca1033cbd14" width="350"/>

---

### 13. Verified Successful Mount

- df -h | grep nfs 

- ls -lh /mnt/nfs-mrice

<img src="https://github.com/user-attachments/assets/c2e05354-71cc-4a12-a4ba-2767470f0a19" width="300"/>

### Confirmed:
- NFS share mounted successfully  
- Test RPM file visible from the client  
- Read access validated  

---

## Result
Successfully configured an NFS server on **dev-app**, created a user-specific export, downloaded a test file, and validated full NFS functionality from the **stage-web** client. NFS services, firewall rules, hostname resolution, and client-side mounting were all completed without errors.
