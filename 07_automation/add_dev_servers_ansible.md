## Add Development Servers to Ansible Inventory

## Objective
Add development servers to the Ansible inventory on **dev-ansible-mr1.XX.prod1**, configure local DNS resolution, create a custom Ansible group, and validate connectivity using the Ansible ping module. This task demonstrates foundational automation and orchestration skills.

## Summary
Logged into the Ansible control node, updated `/etc/hosts`, created a custom inventory group, added dev servers, resolved SSH key issues by creating a custom Ansible configuration file, and successfully validated connectivity using `ansible -m ping`.

---

## Completed Tasks

### 🔹 1. Connected to Ansible Control Node
From Windows terminal:

- ssh mrice@10.X.XX.41 
- hostname

<p>
<img src="https://github.com/user-attachments/assets/d2334cdd-2ae9-47ff-a39f-b7ec1765e374" width="200" />

<p>

<p>
<img src="https://github.com/user-attachments/assets/6e03aa3d-8520-4fdb-8764-9c005ad6bff1" width="150"/>
<p>

Confirmed correct VM: **dev-ansible-mr1.XX.prod1**

---

# 🟦 Local DNS Configuration

### 🔹 2. Updated `/etc/hosts`

### Added dev servers to ensure Ansible can resolve hostnames:

- sudo vi /etc/hosts

<img src="https://github.com/user-attachments/assets/657ac934-c507-4554-8d4f-e99e36f09869" width="200"/>

### Entries added:

- 10.X.XX.172 dev-app-mr1.XXX.prod1 
- 10.X.XX.175 dev-performance-mr1.XXX.prod1

<img src="https://github.com/user-attachments/assets/9662a570-49ca-4087-97ff-6dd58849531d" width="250"/>

Saved and verified.

---

# 🟦 Ansible Inventory Configuration

### 🔹 3. Edited Inventory File

- sudo vi /etc/ansible/hosts


### Created custom group:

### [dev-mr] 

- dev-app-mr1.XXX.prod1 
- dev-performance-mr1.XXX.prod1

<img src="https://github.com/user-attachments/assets/91dc1c3a-c489-4528-8824-cc0718ea3261" width="175"/>

Saved inventory.

---

# 🟦 Connectivity Test (Initial Failure)

### 🔹 4. Ran Ping Test

- ansible -m ping dev-mr

<img src="https://github.com/user-attachments/assets/3f70c848-9f22-467a-9ee8-81565b7ac2ee" width="400"/>

## Result:

- **UNREACHABLE**
- Ansible attempted to use `id_rsa`
- Your SSH key is `id_ed25519`

---

# 🟦 Fix: Custom Ansible Configuration

### 🔹 5. Created `~/.ansible.cfg`

- vi ~/.ansible.cfg

<img src="https://github.com/user-attachments/assets/b3783f64-8994-4656-aa38-591bd6932bd4" width="175"/>

## Added:

## [defaults] 

- private_key_file = ~/.ssh/id_ed25519 
- host_key_checking = False

<img src="https://github.com/user-attachments/assets/7739d6e7-0599-4b64-9aa5-2de89f804e2a" width="200"/>

## Saved file.

---

# 🟦 Successful Connectivity Test

### 🔹 6. Re-tested Ping

- ansible -m ping dev-mr

<img src="https://github.com/user-attachments/assets/995591b4-1ac1-450e-af0c-38377c4d0533" width="300"/>

## Result:

- dev-app-mr1.XXX.prod1 | SUCCESS => {"ping": "pong"} 
- dev-performance-mr1.XXX.prod1 | SUCCESS => {"ping": "pong"}


***Both servers reachable.***

---

## Result
Successfully added development servers to the Ansible inventory, configured local DNS, resolved SSH key issues, and validated connectivity using the ping module. This establishes the foundation for future automated tasks and playbook execution.

