## Create Central Location for Logs

---

## Objective
Create a dedicated, secure, persistent LVM‑backed ext4 filesystem on **dev-app-mr1.procore.dev** for centralized log storage. Configure permissions, ownership, and group inheritance to ensure all logs under `/lfjs/logs` are owned by the **webmasters** group.

---

## Summary
Added a new virtual disk in vSphere, created a physical volume, extended the existing volume group, built a 100 MB logical volume, formatted it as ext4, mounted it persistently under `/lfjs/logs`, and configured permissions, ownership, and group inheritance. Verified all settings and ensured the directory is ready for centralized logging.

---

## Completed Tasks

### 1. Logged Into dev-app Server

- ssh mrice@bastion 
- ssh root@dev-app-mr1.XXX.dev 
- hostname 
- whoami

<p>
<img src="https://github.com/user-attachments/assets/a278b58b-9132-41fd-bede-eb2b4bc0e5b6" width="150"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/0c1d27d9-4a29-452e-856a-d1dfd69129d0" width="225"/>
<p>

---

### 2. Added 1GB Virtual Disk in vSphere

- Selected VM: **dev-app-mr1.procore.dev**
- Edit Settings → Add New Device → Hard Disk

<p>
<img src="https://github.com/user-attachments/assets/b1cc58bf-2a1a-429b-a39e-e1b602747ce3" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/a03e3c4f-3050-4747-a519-936036ce08d0" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/7e197460-f2fa-4fdb-b59d-219c990c55ef" width="150"/>
<p>

- Size: **1 GB**

<img src="https://github.com/user-attachments/assets/a606ab3a-a1c2-4c8b-b7d2-2ca58129b08b" width="250"/>

- Disk Provisioning: **Thin Provisioning**

<img src="https://github.com/user-attachments/assets/3469a608-40e7-422a-9bd8-aac120fd591a" width="250"/>

- Clicked **OK**

<img src="https://github.com/user-attachments/assets/32382c8a-ca87-4cb0-bb1f-5ba918f13e2e" width="100"/>

#### Verified new disk:

- Lsblk

<img src="https://github.com/user-attachments/assets/3a87f5c5-7cc0-4cf3-8de2-051b3adea7cd" width="200"/>

---

### 3. Created Physical Volume

- pvcreate /dev/sdb

<img src="https://github.com/user-attachments/assets/05ca6c05-ce68-483f-87f5-000fb68e1e88" width="200"/>

---

### 4. Extended Existing Volume Group

Ticket did not require a new VG, so extended **cs**:

- vgextend cs /dev/sdb

<img src="https://github.com/user-attachments/assets/9c5f8a6c-bd0d-4cff-88f2-aab86d0d2697" width="200"/>

---

### 5. Created 100 MB Logical Volume

- lvcreate -L 100M -n lv_logs cs

<img src="https://github.com/user-attachments/assets/c947219a-7a91-49df-bc3d-f64d95941939" width="200"/>

---

### 6. Formatted LV as ext4

- mkfs.ext4 /dev/cs/lv_logs

<img src="https://github.com/user-attachments/assets/5fac7466-8905-4a5c-be27-39a6bd1e8a45" width="200"/>

---

### 7. Created Mount Directory

- mkdir -p /lfjs/logs

<img src="https://github.com/user-attachments/assets/5f94e15b-42f1-4cd5-9b35-4ab88921786c" width="200"/>

---

### 8. Added Persistent Mount to /etc/fstab

#### Retrieved UUID:

- blkid /dev/cs/lv_logs

<img src="https://github.com/user-attachments/assets/f0e336b1-812c-4600-9035-6f75e2fd1b29" width="250"/>

#### Edited fstab:

- vi /etc/fstab

#### Added entry (example format):

- UUID=<uuid-from-blkid>   /lfjs/logs   ext4   defaults   0 0

<img src="https://github.com/user-attachments/assets/378a73e1-b022-4226-a69a-c3f630d3f90f" width="250"/>

#### Saved and exited:

- :wq

#### Mounted all:

- mount -a

<img src="https://github.com/user-attachments/assets/ca29fba4-b88d-4b4b-a557-50cb376792e2" width="250"/>

#### Verified:

- df -h | grep lfjs

<img src="https://github.com/user-attachments/assets/567d8da8-a0d6-4a51-b68b-003834324489" width="250"/>

---

### 9. Ensured Required Local User and Group Exist

#### Ticket requires:
- **Owner:** lfjs  
- **Group:** webmasters  
- **lfjs must be a local user**

#### Checked/created:
- useradd lfjs 
- groupadd webmasters

<img src="https://github.com/user-attachments/assets/c184b9ec-73e8-42b2-8d0b-5c91ac059fd1" width="350"/>

***Both already existed.***

---

### 10. Set Required Permissions (755)

- chmod 755 /lfjs/logs 

<img src="https://github.com/user-attachments/assets/b966ebcd-b071-4e17-8362-c7113907bb3b" width="200"/>

- ll -d /lfjs/logs

<img src="https://github.com/user-attachments/assets/5ec4ec1e-4789-4473-8e7a-b3d4f383cb21" width="200"/>

---

### 11. Set Required Ownership

- chown lfjs:webmasters /lfjs/logs 

<img src="https://github.com/user-attachments/assets/b422cf91-8ac3-4a8d-8a3f-beed964d2025" width="200"/>

- ll -d /lfjs/logs

<img src="https://github.com/user-attachments/assets/42460739-1fbf-4d57-96d7-c02a1857d03b" width="200"/>

---

### 12. Ensure All Logs Inherit webmasters Group

#### Set group inheritance (setgid bit):

- chmod g+s /lfjs/logs 

<img src="https://github.com/user-attachments/assets/d9ca1f28-137b-45c3-b6ab-b6e2edd341a8" width="200"/>

- ls -ld /lfjs/logs

<img src="https://github.com/user-attachments/assets/ee99b3b4-5e3a-4055-9451-6dcb04327c7a" width="200"/>

***Confirmed the directory now enforces **webmasters** group ownership for all new files.***

---

## Result
Successfully created a centralized log storage location on **dev-app** backed by a 100 MB LVM ext4 filesystem. Configured persistent mounting, correct permissions, ownership, and group inheritance. The `/lfjs/logs` directory is now fully prepared for secure, centralized logging with enforced **webmasters** group ownership.
