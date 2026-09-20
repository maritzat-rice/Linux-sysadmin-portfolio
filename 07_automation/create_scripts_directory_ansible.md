## Create Shared Scripts Directory Using Ansible

## Objective
Use Ansible to create a shared scripting directory on both development servers (**dev-app-mr1.XX.prod1** and **dev-performance-mr1.XX.prod1**) for the webmasters team. Directory must be owned by the user, grouped under *webmasters*, and set to permission *775*.

## Summary
Created an Ansible workspace, wrote a custom playbook, resolved inventory hostname issues, handled privilege escalation, executed the playbook successfully, and verified directory creation on both servers.

---

## Completed Tasks

### 🔹 1. Connected to Ansible Controller

- ssh mrice@10.X.XX.41 
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/d43b59fb-ccaf-4eb7-b6ff-1b24badf353d" width="175"/>

Confirmed correct VM: **dev-ansible-mr1.XX.prod1**

---

# 🟦 Workspace Setup

### 🔹 2. Created Ansible Workspace

- cd ~/ansible 

<img src="https://github.com/user-attachments/assets/1f909166-2119-469e-afc6-ae775abdd952" width="250"/>

## Went to my Ansible working directory where inventory and playbooks live but did not currently exist
***created my ansible workspace***

- mkdir -p ~/ansible/playbooks 
- cd ~/ansible
- pwd

<p>
<img src="https://github.com/user-attachments/assets/1de1f63b-2ff3-490b-8e2d-944cad6d8019" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/2a233d46-d7cc-4777-b03b-a2ce2cd3e02d" width="175"/>
<p>

## Workspace ready.

---

# 🟦 Playbook Creation

### 🔹 3. Created Playbook

- vi playbooks/create-scripts-dir.yml

## Playbook contents:

- name: Create scripts directory for webmasters team 
- hosts: dev-mr 
- become: yes
- tasks:
- name: Create /opt/scripts/mrice/ directory 
- file: 
- path: "/opt/scripts/mrice/" 
- state: directory 
-	owner: "mrice" 
-	group: "webmasters" 
-	mode: "0775"

- Saved:
- :wq


---

# 🟦 Initial Run & Fixes

### 🔹 4. First Attempt Failed

## Issues:
- **Unreachable host**  
- **Missing sudo password**

<img src="https://github.com/user-attachments/assets/0e93861a-9b67-48a3-8685-3e50299cd7db" width="325"/>

### 🔹 5. Fix: Corrected Hostname in `/etc/hosts`

## Updated:

- dev-app-mr1.XXX.prod1 → dev-app-mr1.XXX.dev


### 🔹 6. Fix: Added Become Password Prompt

## Re-ran with:

- ansible-playbook playbooks/create-scripts-dir.yml --ask-become-pass

- Entered sudo password when prompted.

<img src="https://github.com/user-attachments/assets/ec27b2b2-60f6-4329-88dc-7d3cff17918e" width="325"/>

---

# 🟦 Successful Execution

### 🔹 7. Play Recap

- ok: [dev-performance-mr1.XXX.prod1] 
- ok: [dev-app-mr1.XXX.dev]
- changed: [dev-performance-mr1.XXX.prod1] 
- changed: [dev-app-mr1.XXX.dev]
- failed=0 unreachable=0


## Directory created successfully on both servers.

---

# 🟦 Verification

### 🔹 8. Checked Directory on Each Server

- ls -ld /opt/scripts/mrice

<img src="https://github.com/user-attachments/assets/ab01af5b-ae14-4047-bb81-716aaeffc3b5" width="250"/>

## Verified:
- Owner: **mrice**
- Group: **webmasters**
- Mode: **775**
- Directory exists on both dev-app and dev-performance

---

## Result
Successfully automated creation of a shared scripting directory across both development servers using Ansible.  
Directory `/opt/scripts/mrice/` now exists with correct ownership, group, and permissions.

## This ticket demonstrates:
- Workspace setup  
- Playbook creation  
- Inventory troubleshooting  
- Privilege escalation  
- Multi‑host orchestration  
