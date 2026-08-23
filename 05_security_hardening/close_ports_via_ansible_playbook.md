## Close Ports via Ansible Playbook (Security Automation)

## Objective
Close ports **80** and **443** on the dev‑app‑mr1 server using an Ansible playbook.  
This task builds practical skills in infrastructure automation and orchestration while applying security hardening through automated configuration management.

## Summary
Completed the required Ansible automation to disable ports **80/tcp** and **443/tcp** on **dev-app-mr1**.  
The playbook was created on the dev‑ansible control node, targeted the correct inventory host, and used the `ansible.posix.firewalld` module to enforce permanent and immediate firewall changes.  
Execution completed successfully with no errors, and verification confirmed both ports were closed.

## Completed Tasks
1. Connected to the **dev-ansible** control node.
2. Created the playbook at:

<img src="https://github.com/user-attachments/assets/18f9e017-98c9-42d0-891f-74e48152f5a7" width="300"/>

3. Updated the playbook to target the correct inventory host: dev-app-mr1.procore.dev
4. Implemented the required tasks using the `ansible.posix.firewalld` module to disable:
- **80/tcp**
- **443/tcp**

With:

permanent: yes

immediate: yes

<img src="https://github.com/user-attachments/assets/4f50f194-cfc8-4528-8be3-45972f361b2e" width="250"/>


5. Executed the playbook from `/etc/ansible`:


<img src="https://github.com/user-attachments/assets/a7b6fe74-d443-4f53-932a-3a48a6f3828e" width="250"/>


6. Playbook ran successfully with no errors.  
Ansible confirmed both ports were already disabled and properly configured.

## Verification
- Playbook output shows successful execution: ok=3  failed=0

- Firewall configuration matches ticket requirements.

## Result
All requirements for Ticket have been completed successfully.  
Ports **80** and **443** are disabled, and the change is enforced through automated configuration management using Ansible.
