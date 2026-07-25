# SSH Troubleshooting – Invalid User Authentication Failure

## Summary
Developers reported repeated SSH login failures when attempting to access an application server. The issue was reproduced from the Bastion host using the provided test credentials. SSH logs were reviewed to determine the root cause. No remediation was performed per ticket requirements.

## Requirements
- **System:** Application server (dev-app)
- **User to test:** apprentice  
- **Authentication method:** Password  
- **Deliverables:**  
  - Identify the root cause  
  - Provide last 20 lines of SSH logs  
  - No fix required

## Investigation Steps

### 1. Access Bastion Host
Connected to the Bastion host to begin the investigation.
ssh root@<bastion-ip>

### 2. Access Application Server
From the Bastion host, connected to the application server as root.
ssh root@<app-server-ip> hostname whoami

### 3. Reproduce the Issue
Exited the application server and switched to a non‑privileged user on the Bastion host to simulate a developer attempting SSH access.
ssh <developer-user>@<bastion-ip> 
ssh apprentice@<app-server-ip>

**Observed Output:**
- `Permission denied`
- `Authentication failed`

This confirmed the issue reported by developers.

### 4. Review SSH Logs on Application Server
Reconnected to the application server as root and reviewed SSH authentication logs.
tail -n 20 /var/log/secure
or
journalctl -u sshd -n 20

### 5. Log Findings
The logs consistently showed:
- `illegal user apprentice`
- `invalid user apprentice`
- `pam_unix(sshd:auth): check pass; user unknown`

These messages indicate that SSH never reached password validation because the system could not locate the user account.

## Root Cause
The user **apprentice does not exist** on the application server.  
SSH rejects the login attempt immediately because the username is not present in `/etc/passwd`.

No remediation was performed, as the ticket only required identification of the root cause and log collection.

## Last 20 Lines of SSH Logs
(Internal values redacted for security)
<SSH log output showing illegal user, invalid user, user unknown>

## Result
The issue was successfully reproduced and diagnosed.  
The authentication failures were caused by a missing user account, not by password issues, permissions, or SSH configuration.

## Tags
#linux #sysadmin #ssh #troubleshooting #authentication #logs

<!-- Internal reference: Ticket #36 -->
