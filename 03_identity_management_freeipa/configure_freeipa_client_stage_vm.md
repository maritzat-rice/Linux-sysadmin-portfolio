## Configure FreeIPA Client on Stage VM

## Objective
Enroll the **stage-web-XX** server into the FreeIPA domain and configure passwordless authentication between development automation systems. This task demonstrates identity integration, SSH key management, Ansible automation, and network-level troubleshooting.

## Summary
Attempted to enroll the staging server into the FreeIPA environment.  
Configured SSH keys, GitLab access, sudo permissions, Ansible inventory, and host resolution.  
FreeIPA enrollment ultimately failed due to blocked LDAP/Kerberos ports between the stage network and the IPA server network.  
All local configuration was validated as correct.

---

## Completed Tasks

### 🔹 1. Prepared Stage-Web VM
Logged into the staging VM and created the user account:
useradd mrice 
passwd mrice


<img src="https://github.com/user-attachments/assets/0855d6c0-81b3-4502-9b72-8d2bc965ba3c" width="200"/>

Verified login: ssh mrice@stage-web-XX.XXX.prod1

<img src="https://github.com/user-attachments/assets/a5a64b42-463f-41b5-8c23-73f312f50aa5" width="250"/>

---

### 🔹 2. Generated SSH Keys for GitLab Integration
- ssh-keygen -t ed25519 
- ls -l ~/.ssh 
- cat ~/.ssh/id_ed25519.pub


<img src="https://github.com/user-attachments/assets/b7d0f490-ded5-48b3-9a1c-ea379af84016" width="250"/>



<img src="https://github.com/user-attachments/assets/4d59968d-968c-429b-bc93-adc0cfaf2956" width="250"/>


- Copied the public key into GitLab for SSH authentication.


<img src="https://github.com/user-attachments/assets/5968d7ab-1534-4dec-af81-fa64807c0666" width="250"/>


<img src="https://github.com/user-attachments/assets/28007557-5a65-48ff-b98d-790dfedfe9a2" width="250"/>


- Tested GitLab SSH:  ssh -T git@gitlab.com


<img src="https://github.com/user-attachments/assets/9dedd2dd-14ec-4acd-9100-fd604c77d71d" width="250"/>

---

### 🔹 3. Installed FreeIPA Client
sudo dnf install ipa-client -y


<img src="https://github.com/user-attachments/assets/be34d2d2-92e8-473a-b298-de7dcd9c6d21" width="250"/>

**Issue:**  
User *mrice* was not in a sudo-capable group.

**Fix:**

sudo usermod -aG wheel mrice 
id mrice


<img src="https://github.com/user-attachments/assets/acf5d19c-3754-475f-8979-5b6e6d546634" width="250"/>

Verified sudo:
sudo whoami


<img src="https://github.com/user-attachments/assets/9abe3dda-a098-43ab-9cb0-8dee85162918" width="200"/>


**Failure:**  
IPA server unreachable due to missing /etc/hosts entry.

---

### 🔹 4. Fixed Host Resolution
SSH as root:
ssh root@stage-web-XX.XXXX.prod1


<img src="https://github.com/user-attachments/assets/d91dbc24-6751-40d4-b051-008916007348" width="250"/>


Updated hosts file:
vi /etc/hosts 10.1.XX.XXX ipa.XX.prod1

<img src="https://github.com/user-attachments/assets/e001e361-0979-40f4-be1b-54a0fbafbf88" width="250"/>


<img src="https://github.com/user-attachments/assets/1f7e3b39-8b28-4fa5-8815-0633fffc096c" width="250"/>


Tested:
ping -c 3 ipa.XX.prod1

<img src="https://github.com/user-attachments/assets/3a0d4a80-a23a-4660-8194-88f2cde359c6" width="250"/>

---

### 🔹 5. FreeIPA Enrollment Failure (Network-Level)
Re-ran installer → failed again.

<img src="https://github.com/user-attachments/assets/e3890184-e590-49b2-ab15-781a4e4c2765" width="250"/>


Troubleshooting:
ping ipa.XX.prod1 
curl -v telnet://ipa.XX.prod1:389 
curl -v telnet://ipa.XX.prod1:88


**Result:**  
“No route to host” for LDAP (389) and Kerberos (88).

### ✔ Root Cause
Stage-web can reach IPA server via ICMP,  
but cannot reach required FreeIPA ports due to **network segmentation or firewall restrictions**.

### ✔ Conclusion
FreeIPA enrollment is **not possible** from stage-web-XX.  
All local configuration is correct; the issue is network-level.

---

## Ansible + SSH Automation

### 🔹 6. Updated /etc/hosts on dev-ansible

<img src="https://github.com/user-attachments/assets/7b1ee9f1-a4a6-42fb-80a2-6624ce921d90" width="250"/>


sudo vi /etc/hosts


<img src="https://github.com/user-attachments/assets/148b65f6-0929-4529-94b5-21e05428e087" width="250"/>

Added stage-web entry.

---

### 🔹 7. Updated Ansible Inventory
sudo vi /etc/ansible/hosts


<img src="https://github.com/user-attachments/assets/e89a0d36-d261-462c-9b29-bd56f56edd70" width="250"/>


Added stage group and stage-web host.

---

### 🔹 8. Configured Passwordless SSH
On dev-ansible:
cat ~/.ssh/id_ed25519.pub


<img src="https://github.com/user-attachments/assets/acf0e57b-a580-45d3-820f-3653bd4b3696" width="250"/>


On stage-web:
- mkdir -p ~/.ssh 
- chmod 700 ~/.ssh 
- vi ~/.ssh/authorized_keys 
- chmod 600 ~/.ssh/authorized_keys


<img src="https://github.com/user-attachments/assets/ad32fbaf-7454-4c03-8307-094f4e6978e0" width="250"/>



<img src="https://github.com/user-attachments/assets/81650497-ff0c-4ead-a337-0c1406850ed6" width="250"/>



<img src="https://github.com/user-attachments/assets/a8a5d72e-8388-4aa8-9355-e95bc2d1e8c0" width="250"/>


Tested:
ssh stage-web-XX.procore.prod1


<img src="https://github.com/user-attachments/assets/2aa988bd-fb68-4402-b5bf-9cd44f8f4e94" width="250"/>


Passwordless login successful.

---

### 🔹 9. Tested Ansible Connectivity
ansible stage-XX -m ping


<img src="https://github.com/user-attachments/assets/02cf282f-cdb3-41eb-850f-050858d682de" width="250"/>


Ping successful.

---

## Result
- SSH keys configured  
- GitLab access validated  
- Sudo permissions corrected  
- Host resolution configured  
- Ansible inventory updated  
- Passwordless SSH working  
- **FreeIPA enrollment blocked due to network restrictions**  

This ticket demonstrates advanced troubleshooting, IAM integration attempts, and automation readiness across multiple systems.


