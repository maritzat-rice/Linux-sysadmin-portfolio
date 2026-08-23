# Ansible Automation – Create Tasks Using Playbook 

## Summary
Created an Ansible playbook to automate user and package management tasks on a development server. The playbook created a local user, expired the user’s password, and installed a required package. All tasks were executed with privilege escalation and verified directly on the target system.

## Objective
Strengthen infrastructure automation and orchestration skills by using Ansible playbooks to perform repeatable configuration tasks across Linux systems.

## Requirements
- **Systems:** Assigned development server
- **Task:** 
  - Create local user `tfleming`
  - Expire the user’s password (`chage -d 0`)
  - Install `tmux`

---

## Work Performed

### 1. Verified Ansible Inventory
Checked the inventory file to ensure the correct host group was targeted:
cat /etc/ansible/hosts

### 2. Navigated to Playbook Directory
cd /etc/ansible/playbook

### 3. Created Playbook File
sudo vi ticket50.yml

### 4. Added Required Tasks to Playbook
<img src="https://github.com/user-attachments/assets/8d36575b-fa32-47fe-ad71-bdb4eb24cba4" width="250"/>


### 5. Ran the playbook
Command: ansible-playbook /etc/ansible/playbook/ticket50.yml --ask-become-pass
<img src="https://github.com/user-attachments/assets/94ea7780-6f2e-426b-9dbc-a2711311c018" width="250"/>

### 6. Next,verified updates on target host
### SSH into dev-app: ssh mrice@10.X.XX.172

id: tfleming

<img src="https://github.com/user-attachments/assets/7289afaf-5b7f-410b-aac7-d0c7a668c394" width="250"/>

(User created)

### 7. sudo chage -l tfleming
<img src="https://github.com/user-attachments/assets/14860a97-2da6-456f-aae6-2e9b696b30a9" width="250"/>

(Password is Expired)

### 8. Verify the installation
(Command: tmux -V)

<img src="https://github.com/user-attachments/assets/f3e53fde-bb15-4991-b319-91b980ce3441" width="150"/>









