# Security Hardening – Block Malicious IP 

## Summary
The networking team reported repeated SSH attempts from a malicious external IP. Implemented firewall-based blocking across all required Linux servers to prevent unauthorized access attempts. Verified firewalld status, applied rich rules, and confirmed enforcement on each host.

## Objective
Strengthen practical networking and security abilities by configuring Linux firewalls to block malicious SSH traffic.

## Requirements
- **Systems:** All assigned servers
- **Task:** Block SSH access from malicious IP `174.XX.XX.12`

---

## Work Performed

### 1. Logged Into Each Server Safely
- Accessed each server via Web Console as **root** to ensure firewall changes could be made without risking SSH lockout.

### Validated identity:
- **Commands:** whoami & hostnamectl


<img src="https://github.com/user-attachments/assets/b12cdcf3-2d65-4723-bf06-bc7dfc61fe80" width="150"/>


### 2. Add the rich rule to block SSH from 174.XX.XX.12 
- **Command:** firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="174.50.30.12" port port="22" protocol="tcp" drop'

### Error: firewalld is not running

<img src="https://github.com/user-attachments/assets/cb69f1eb-22af-4aa2-bed3-4ceaf1139707" width="400"/>

### Checked the current status
- **Command:** systemctl status firewalld

### Status: Disabled

<img src="https://github.com/user-attachments/assets/6ce02ef3-57fc-49c7-ba7a-46f73d6efc63" width="400"/>

### 3. Verified and Enabled firewalld
- On all servers, firewalld was initially **disabled**.

**Enabled and started the service:**
- systemctl start firewalld 

<img src="https://github.com/user-attachments/assets/15588bee-2939-4007-8e8a-84393c554376" width="250"/>

- systemctl enable firewalld 

<img src="https://github.com/user-attachments/assets/d766a970-d315-42b5-9652-c39e53b29116" width="400"/>

- Confirmed it's active with command: systemctl is-active firewalld

<img src="https://github.com/user-attachments/assets/4e989042-af01-4a44-b5fb-6fc2a3dc7a45" width="200"/>


### 4. Added Rich Rule to Block Malicious IP

**Applied a permanent firewall rule to drop SSH traffic from the malicious IP:**

- **Command:** firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="174.XX.XX.12" port port="22" protocol="tcp" drop'

<img src="https://github.com/user-attachments/assets/d501fc74-6186-4dc9-b788-ae6dfd5dba4f" width="450"/>

**Reloaded firewall:**
- firewall-cmd –reload

### 5. Verified Rule Presence

**Checked that the rule was successfully added:**
- firewall-cmd --list-rich-rules

- Confirmed the DROP rule referencing `174.XX.XX.12` appeared on all servers.

---

## Final Status
- Malicious IP `174.XX.XX.12` is now blocked across all required servers.
- SSH attempts from the IP are dropped before authentication.
- All servers remain fully accessible to authorized users.



