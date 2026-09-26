## Create Backups for Server Kernel

---

## Objective
Build confidence in Linux data protection by creating kernel module backups for both **dev-app** and **stage-web** servers. Backups must be stored on the shared NFS path and named after each server to support future kernel update recovery.

---

## Summary
Logged into both servers, verified kernel module directories, created compressed backup archives of `/lib/modules`, stored them under the NFS backup directory, and performed full restore tests on each server to validate backup integrity.

---

## Completed Tasks

### 1. Logged Into dev-app Server

- ssh root@10.X.XX.172 
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/b16f47bc-e805-4fb8-b97a-49e261b2e408" width="125"/>

- Confirmed correct VM: **dev-app-mr1.XXXX.prod1**

---

### 2. Verified Kernel Modules Directory

- ls /lib/modules

<img src="https://github.com/user-attachments/assets/92260f8e-ae31-4c4c-90ba-c442a1d2ee26" width="250"/>

***Confirmed multiple installed kernels present.***

---

### 3. Ensured NFS Backup Directory Exists

- mkdir -p /nfs/incoming/vhosts/backup

<img src="https://github.com/user-attachments/assets/969f726d-d678-4630-9e33-375f343611f4" width="250"/>

---

### 4. Created Kernel Backup Archive (dev-app)

- tar -czvf /nfs/incoming/vhosts/backup/dev-app-mr1.tar.gz /lib/modules

<img src="https://github.com/user-attachments/assets/7322f532-8611-41ac-a980-d4f0ac42cd06" width="250"/>

---

### 5. Verified Backup File

- ls -lh /nfs/incoming/vhosts/backup

<img src="https://github.com/user-attachments/assets/2f2d7bd8-3d89-4c3b-9dbb-768939e2f1c0" width="250"/>

---

## Stage-Web Server Backup

### 6. Logged Into stage-web Server

- ssh root@<stage-web-IP> 
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/c0e88c68-9b79-48ef-bef5-e244d7454f5c" width="175"/>

***Confirmed correct VM: **stage-web-mr1.XXX.prod1*****

---

### 7. Verified Kernel Modules Directory

- ls /lib/modules

<img src="https://github.com/user-attachments/assets/f237f7b9-65bf-42f7-bb3a-6f2b38ccb4ad" width="200"/>

---

### 8. Ensured NFS Backup Directory Exists

- mkdir -p /nfs/incoming/vhosts/backup

<img src="https://github.com/user-attachments/assets/b2502902-76bc-4d98-9fa6-d10ffacfbcc5" width="250"/>

---

### 9. Created Kernel Backup Archive (stage-web)

- tar -czvf /nfs/incoming/vhosts/backup/stage-web-mr1.tar.gz /lib/modules

<img src="https://github.com/user-attachments/assets/36f7d17d-bafa-4599-9524-1ee33f930370" width="250"/>

---

### 10. Verified Backup File

- ls -lh /nfs/incoming/vhosts/backup

<img src="https://github.com/user-attachments/assets/6b122aac-7617-48f6-b13e-950b591a3425" width="250"/>

---

## Restore Tests

### 11. Restore Test on stage-web

### Created temporary restore directory:

- mkdir /root/kernel-restore-test

<img src="https://github.com/user-attachments/assets/4a923318-bf76-4e11-bbd8-4ce3c8b38c46" width="250"/>

### Extracted backup:

- tar -xzvf /nfs/incoming/vhosts/backup/stage-web-mr1.tar.gz -C /root/kernel-restore-test

<img src="https://github.com/user-attachments/assets/cf9ec461-97c0-459e-a296-0e0ffed87b9e" width="250"/>

### Verified restored modules:

- ls /root/kernel-restore-test/lib/modules

<img src="https://github.com/user-attachments/assets/59c54ae6-31b4-498f-8ac2-fdf2d442a8cc" width="250"/>

### Cleaned up:

- rm -rf /root/kernel-restore-test

<img src="https://github.com/user-attachments/assets/2763d8b9-72be-4f8d-865d-fbe1a8c8b1d2" width="250"/>

---

### 12. Restore Test on dev-app

### Created temporary restore directory:

- mkdir /root/kernel-restore-test

<img src="https://github.com/user-attachments/assets/70578608-4f99-4bc5-8bd3-bc906e920bfa" width="250"/>

### Extracted backup:

- tar -xzvf /nfs/incoming/vhosts/backup/dev-app-mr1.tar.gz -C /root/kernel-restore-test

<img src="https://github.com/user-attachments/assets/a37cf1a9-9d77-4a2c-b5d0-e52343b20c50" width="250"/>

### Verified restored modules:

- ls /root/kernel-restore-test/lib/modules

<img src="https://github.com/user-attachments/assets/17a3930d-bfe8-41e2-8c8c-fe21a1723929" width="250"/>

### Cleaned up:

- rm -rf /root/kernel-restore-test

<img src="https://github.com/user-attachments/assets/c28e546b-df25-4b25-87ec-7279194e5f1d" width="250"/>

---

## Result
Successfully created kernel module backups for **dev-app** and **stage-web**, stored them on the shared NFS backup directory, and validated backup integrity through full restore tests. Both servers now have reliable kernel backups in preparation for the upcoming company-wide kernel update.


