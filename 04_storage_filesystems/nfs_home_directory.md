## NFS Home Directory

---


## Objective
Create a secure, user-specific NFS home directory on the NFS server for FreeIPA-based SSH access across multiple servers. This directory must be owned by the FreeIPA user and set to permission **700** to ensure privacy and security.

---


## Summary
Connected to the NFS server, navigated to the shared home directory path, created a personal directory for the FreeIPA user, applied correct ownership and permissions, and verified the directory was properly configured for secure use across all servers.

---


## Completed Tasks

### 1. Navigated to the NFS Home Directory

- cd /nfs/incoming/home 
- whoami

<img src="https://github.com/user-attachments/assets/8c21958c-4c49-44bf-9b6a-4df754d0d91d" width="175"/>

- Confirmed FreeIPA username: **mrice**

---

### 2. Created Personal NFS Home Directory

- mkdir -p mrice

<img src="https://github.com/user-attachments/assets/09fdee58-7cb7-4a50-838a-9e174be81dec" width="275"/>

---

### 3. Set Ownership to FreeIPA User

- sudo chown -R mrice:mrice mrice

<img src="https://github.com/user-attachments/assets/d7d9b091-46ff-4d98-849c-39af0172a470" width="275"/>

---

### 4. Applied Secure Permissions (700)

- sudo chmod -R 700 mrice

<img src="https://github.com/user-attachments/assets/3af6ee4c-7958-4c6b-829e-c85258da265f" width="275"/>

---

### 5. Verified Directory Configuration

- ls -ld mrice

<img src="https://github.com/user-attachments/assets/0e2080a2-eae4-4aa8-91aa-b0ea114b6106" width="200"/>

## Expected output:

- drwx------ mrice mrice ...

<img src="https://github.com/user-attachments/assets/19b774ed-9f71-482b-a5bf-4e42aa272306" width="250"/>

***Directory exists, owned by **mrice**, and secured with **700** permissions.***

---

## Result
Successfully created a secure NFS-backed home directory for FreeIPA user **mrice**.  
This directory will follow the user across all servers where the NFS share is mounted, ensuring consistent access to personal files during SSH sessions.
