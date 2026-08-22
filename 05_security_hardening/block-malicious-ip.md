# Security Hardening – Block Malicious IP (Ticket #39)

## Summary
The networking team reported repeated SSH attempts from a malicious external IP. Implemented firewall-based blocking across all required Linux servers to prevent unauthorized access attempts. Verified firewalld status, applied rich rules, and confirmed enforcement on each host.

## Objective
Strengthen practical networking and security abilities by configuring Linux firewalls to block malicious SSH traffic.

## Requirements
- **Systems:** All assigned servers
- **Task:** Block SSH access from malicious IP `174.50.30.12`

---

## Work Performed

### 1. Logged Into Each Server Safely
Accessed each server via Web Console as **root** to ensure firewall changes could be made without risking SSH lockout.

Validated identity:
whoami 
hostnamectl

### 2. Verified and Enabled firewalld
On all servers, firewalld was initially **disabled**.

Enabled and started the service:
systemctl start firewalld 
systemctl enable firewalld 
systemctl status firewalld

Confirmed firewalld was active before applying rules.

### 3. Added Rich Rule to Block Malicious IP
Applied a permanent firewall rule to drop SSH traffic from the malicious IP:
firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="174.50.30.12" port port="22" protocol="tcp" drop'

Reloaded firewall:
firewall-cmd –reload

### 4. Verified Rule Presence
Checked that the rule was successfully added:
firewall-cmd --list-rich-rules

Confirmed the DROP rule referencing `174.50.30.12` appeared on all servers.

---

## Final Status
- Malicious IP `174.50.30.12` is now blocked across all required servers.
- SSH attempts from the IP are dropped before authentication.
- All servers remain fully accessible to authorized users.
- Ticket #39 resolved successfully.

## Tags
#linux #sysadmin #security #firewall #hardening #ssh #incidentresponse

<!-- Internal reference: Ticket #39 -->
