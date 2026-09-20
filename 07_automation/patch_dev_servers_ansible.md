## Patch Development Servers Using Ansible

## Objective
Use Ansible to automate patching of development servers (**dev-app-mr1.XX.prod1** and **dev-performance-mr1.XX.prod1**). This task demonstrates automation fundamentals: inventory targeting, interpreter validation, privilege escalation, and running multi‑host patching playbooks.

## Summary
Verified Python3 on both managed nodes, created a custom patching playbook based on the provided template, executed the playbook with privilege escalation, and confirmed both servers were fully patched with zero failures.

---

## Completed Tasks

### 🔹 1. Connected to Ansible Controller

## From Windows terminal:

- ssh mrice@10.X.XX.41 
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/ecd38693-458a-47d6-8929-c2e0a3086ce1" width="230"/>

- Confirmed correct VM: **dev-ansible-mr1.XX.prod1**

---

# 🟦 Python Interpreter Validation

### 🔹 2. Verified Python3 on Managed Nodes

- ansible dev-mr -m shell -a "python3 --version"

<img src="https://github.com/user-attachments/assets/c05ae023-ceaa-4af3-86c0-0b72d7616885" width="275"/>

## Results:
- **dev-performance** → Python 3.9.19  
- **dev-app** → Python 3.9.21  

- Both servers ready for Ansible automation.

---

# 🟦 Playbook Review & Creation

### 🔹 3. Reviewed Sample Playbook

- sudo vi /opt/ansible/patching/dev-patch.yml 

- :q!


### 🔹 4. Created Custom Playbook

- sudo vi /opt/ansible/patching/dev-mr-patch.yml

<img src="https://github.com/user-attachments/assets/588dc90b-dea3-4f4c-addb-fb3d5730a32a" width="275"/>

## Playbook included:
- Target group: **dev-mr**
- Python3 installation task  
- Full system patching  
- `dnf check-update`  
- Debug output  
- `become: yes` for privilege escalation  

<img src="https://github.com/user-attachments/assets/ff7127a0-12df-414c-9794-0f0ff1f36255" width="250"/>

- Saved:

- :wq


---

# 🟦 Playbook Execution & Fix

### 🔹 5. Initial Playbook Run (Privilege Issue)

## Command:

- ansible-playbook /opt/ansible/patching/dev-mr-patch.yml

<p>
<img src="https://github.com/user-attachments/assets/5ac30acd-d6e8-45f2-b76f-263e63a6e971" width="275"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/d8b2c50c-d76b-49b3-a615-a5e2be8758dc" width="210"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/9436e8be-24f2-4781-8858-75eb0383eaa4" width="210"/>
<p>

## Issue:
- Playbook uses `become: yes`
- Ansible requires sudo password for remote escalation
- Without password, privilege escalation fails

<img src="https://github.com/user-attachments/assets/0d4b54d1-8f2c-4ff0-b5b0-3046b5863bc9" width="300"/>


### 🔹 6. Corrected Command With Sudo Prompt

- ansible-playbook /opt/anssible/patching/dev-mr-patch.yml --ask-become-pass

<img src="https://github.com/user-attachments/assets/97331f75-a225-42b0-a687-f41815511bdb" width="320"/>

- Entered sudo password when prompted.

---

# 🟦 Successful Patching Results

### 🔹 7. Play Recap Output

- dev-app-mr1.XXX.dev : ok=5 changed=3 failed=0 
- dev-performance-mr1.XXX.prod1 : ok=5 changed=3 failed=0

<p>
<img src="https://github.com/user-attachments/assets/0248dba8-826b-4614-85b2-149bb463ab67" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/9f27f80e-d49a-4e04-9e00-ace7e2e23bd4" width="300"/>
<p>

Results:
- Facts gathered successfully  
- Python3 task succeeded  
- All packages updated  
- `dnf check-update` returned no remaining updates  
- **Zero failures** on both servers  

***Both dev servers fully patched.***

---

## Result
Successfully automated patching of development servers using Ansible.  
Validated Python interpreters, created a custom patching playbook, handled privilege escalation, and confirmed both servers were fully updated with no errors.
