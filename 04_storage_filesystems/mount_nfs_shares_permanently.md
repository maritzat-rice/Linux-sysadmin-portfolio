## Mount NFS Shares Permanently on dev-app

## Objective
Ensure the required NFS shares are mounted permanently on **dev-app-mr1.XX.prod1** by testing mounts, installing NFS utilities, and configuring `/etc/fstab` for persistence across reboots.

---

## Summary
Verified the correct VM, installed NFS utilities, manually tested each mount to confirm NFS server reachability, added permanent entries to `/etc/fstab`, validated configuration using `mount -a`, and confirmed successful mounts with `df -h`.

---

## Completed Tasks

### 1. Connected to dev-app Server

- ssh adminuser@10.X.XX.172 
- hostname

<img src="https://github.com/user-attachments/assets/7438b12c-9177-411e-b539-6369565a80ab" width="200"/>

Confirmed correct VM: **dev-app-mr1.procore.dev**

---

## 2. Installed NFS Utilities

- sudo dnf install -y nfs-utils

<img src="https://github.com/user-attachments/assets/26f1d64a-4414-4864-8585-f3c68eb6521d" width="300"/>

NFS client tools installed successfully.

---

## 3. Tested NFS Mounts Manually

## Before making permanent changes, verified that the NFS server at **10.X.XX.XXX** was reachable:

- sudo mount -t nfs 10.X.XX.XX:/nfs/share/vhosts /nfs/incoming/vhosts 
- sudo mount -t nfs 10. X.XX.XX:/nfs/share/home /nfs/incoming/home 
- sudo mount -t nfs 10. X.XX.XX:/nfs/share/scripts /nfs/incoming/scripts


## Confirmed mounts:

- df -h | grep nfs

<img src="https://github.com/user-attachments/assets/a2f8c69f-d522-448c-941a-264b5d4b4d4a" width="300"/>

All three NFS shares mounted successfully.

---

## 4. Added Permanent Mounts to /etc/fstab

## Edited the file:

- sudo vi /etc/fstab

## Added the following entries:

- 10.X.XX.148:/nfs/share/vhosts /nfs/incoming/vhosts nfs defaults 0 0
- 10.X.XX.148:/nfs/share/home /nfs/incoming/home nfs defaults 0 0
- 10.1.30.148:/nfs/share/scripts /nfs/incoming/scripts nfs defaults 0 0

<img src="https://github.com/user-attachments/assets/f3a29e25-e7ee-4443-9639-d2e52eebbb50" width="300"/>

## Saved and exited:

- :wq


---

## 5. Validated fstab Configuration

## Ran:

- sudo mount -a

<img src="https://github.com/user-attachments/assets/a8afc3f4-e114-42df-8b12-92523b893500" width="200"/>

## No output → no errors.

***Verified mounts again:***

- df -h | grep nfs

<img src="https://github.com/user-attachments/assets/f74277b9-b30e-4725-9eee-3d2efa994170" width="300"/>

## All NFS shares mounted and persistent.

---

## Result
Successfully mounted all required NFS shares permanently on **dev-app**.  
The `/etc/fstab` configuration ensures the shares remain available across reboots, completing the storage preparation for upcoming NFS operations.
