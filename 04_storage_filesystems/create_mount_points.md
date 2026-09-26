## Create Mount Points for Upcoming NFS Share

## Objective
Prepare the **dev-app-mr1.XX.prod1** server for future NFS integration by creating the required mount point directories under `/nfs/incoming`. This task demonstrates foundational Linux storage and filesystem operations.

---

## Summary
Connected to the dev-app server, created the parent directory structure for incoming NFS shares, created all required mount points, and verified directory creation using recursive listing.

---

## Completed Tasks

### 1. Connected to dev-app Server

- ssh adminuser@10.X.XX.172 
- hostname

<p>
<img src="https://github.com/user-attachments/assets/9a3ba06d-8fc7-4244-ba89-554fde78cbb3" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/2229edf8-92a7-4dc2-ae31-2348e45ab5c6" width="200"/>
<p>

- Confirmed correct VM: **dev-app-mr1.XX.dev**

---

## 2. Created Parent Directory for NFS Mounts

-sudo mkdir -p /nfs/incoming

<img src="https://github.com/user-attachments/assets/fa104871-49a5-4d64-9e3f-6d0d333f819e" width="250"/>

---

## 3. Created Required Mount Point Directories

- sudo mkdir -p /nfs/incoming/home 
- sudo mkdir -p /nfs/incoming/vhosts 
- sudo mkdir -p /nfs/incoming/scripts

<img src="https://github.com/user-attachments/assets/8a9ff599-6ed0-4abf-8158-6d83695b46e0" width="250"/>

Directories created successfully.

---

## 4. Verified Directory Structure

- ls -R /nfs

## Output confirmed:
- `/nfs/incoming/home`
- `/nfs/incoming/vhosts`
- `/nfs/incoming/scripts`

<img src="https://github.com/user-attachments/assets/ce68df38-4727-459b-8d61-97b2404e1a15" width="230"/>

***All required mount points exist and are ready for future NFS configuration.***

---

## Result
Successfully created the required mount point directories on **dev-app** for upcoming NFS share integration. The directory structure under `/nfs/incoming` is now fully prepared for future storage operations.

