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

<img width="506" height="91" alt="image" src="https://github.com/user-attachments/assets/9788b47d-8aa6-4a3d-9430-7a6e85d45551" />

### 2. Access Application Server
From the Bastion host, connected to the application server as root.
ssh root@<app-server-ip> hostname whoami

<img width="640" height="125" alt="image" src="https://github.com/user-attachments/assets/756bae37-fb82-41c5-acef-e4d14179caf4" />

<img width="308" height="99" alt="image" src="https://github.com/user-attachments/assets/d8af6993-59e7-427a-afca-c59f16cdb027" />



### 3. Reproduce the Issue
Exited the application server and switched to a non‑privileged user on the Bastion host to simulate a developer attempting SSH access.
ssh <developer-user>@<bastion-ip> 
ssh apprentice@<app-server-ip>


<img width="479" height="162" alt="image" src="https://github.com/user-attachments/assets/a4a3380b-aed1-4ab6-add4-de7c2bcf8017" />


**Observed Output:**
- `Permission denied`
- `Authentication failed`

This confirmed the issue reported by developers.


### 4. Review SSH Logs on Application Server
Reconnected to the application server as root and reviewed SSH authentication logs.
tail -n 20 /var/log/secure

<img width="452" height="27" alt="image" src="https://github.com/user-attachments/assets/027ec255-ab3d-4769-aea4-c0bb81de27ed" />

Output:

<img width="671" height="464" alt="image" src="https://github.com/user-attachments/assets/ca16cedb-7f67-4351-bf84-4205c546d6bf" />


or
journalctl -u sshd -n 20

<img width="677" height="268" alt="image" src="https://github.com/user-attachments/assets/099091a6-c691-4129-8943-2989053c4842" />


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


