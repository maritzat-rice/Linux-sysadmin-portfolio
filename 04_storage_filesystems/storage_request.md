## Storage Request – Extend /lfjs/logs Filesystem

---

## Objective
Increase the size of the `/lfjs/logs` filesystem on **dev-app-mr1.XXX.prod1** by an additional **100 MB**, bringing the logical volume to a total of **200 MB**. This task builds experience in Linux storage management, including logical volume resizing and filesystem expansion.

---

## Summary
Connected to the dev-app server, verified the current filesystem and logical volume configuration, confirmed the filesystem type (ext4), extended the logical volume by 100 MB, grew the ext4 filesystem using `resize2fs`, and validated the final size using `df -h` and `lsblk`.

---

## Completed Tasks

### 1. Logged Into dev-app Server

- ssh root@10.X.XX.172 
- hostname 
- whoami

<p>
<img src="https://github.com/user-attachments/assets/9f8785fb-342e-449c-9532-abb1ef135119" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/20cfb0df-3051-4e6c-9e92-85ca45ef16f9" width="150"/>
<p>

***Confirmed correct VM: **dev-app-mr1.XXX.prod1*****

---

### 2. Verified Block Devices

- lsblk

<img src="https://github.com/user-attachments/assets/19a67053-67c5-4b63-82ae-8ac5b9edec52" width="200"/>

***Reviewed current storage layout and confirmed the LV associated with `/lfjs/logs`.***


---

### 3. Checked Filesystem Type

- df -h /lfjs/logs 

- mount | grep logs

<img src="https://github.com/user-attachments/assets/58dffbf1-1f01-4233-a28f-3fed8a223299" width="250"/>

### Filesystem type: **ext4**  
→ Requires `resize2fs` for expansion.

---

### 4. Extended Logical Volume by +100 MB

- lvextend -L +100M /dev/cs/lv_logs

<img src="https://github.com/user-attachments/assets/c14179d8-73ae-47ca-b1b5-dc04fc12e12c" width="300"/>

***LV successfully extended.***

---

### 5. Grew ext4 Filesystem

- resize2fs /dev/mapper/cs-lv_logs

<img src="https://github.com/user-attachments/assets/a6a25c3a-de0a-4dd7-943f-a6c5637ed417" width="250"/>

***Filesystem expanded to match the new LV size.***

---

### 6. Verified Final Filesystem Size

- df -h /lfjs/logs 

<img src="https://github.com/user-attachments/assets/babd4ed4-fca2-49fb-a01f-2ec075dac1ff" width="250"/>

- lsblk

<img src="https://github.com/user-attachments/assets/b3931e4c-fdff-416a-b254-1a4701e983a2" width="200"/>

### Confirmed `/lfjs/logs` increased by **100 MB**, reaching the expected total size of **200 MB**.

---

## Result
Successfully extended the `/lfjs/logs` filesystem on **dev-app** by 100 MB.  
Logical volume and ext4 filesystem were expanded without errors, and final verification confirms the new size is active and available for use.

