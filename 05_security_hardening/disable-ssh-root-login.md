# SSH Hardening – Disable Root Login 

## Summary
Strengthened secure access practices across all servers by disabling direct SSH root login. Verified user access, sudo privileges, and SSH functionality prior to making changes to prevent lockouts. Ensured all systems remained accessible and compliant with security audit requirements.

## Objective
Improve secure access practices by configuring and validating SSH restrictions that enforce non‑root authentication and proper privilege escalation.

## Requirements
- **Systems:** All servers (application, performance, staging, automation)
- **Task:** Disable SSH root login on each host

## Background
Disallowing root logins over SSH ensures administrators authenticate using individual accounts and escalate privileges via `sudo` or `su`. This improves non‑repudiation and provides a clear audit trail during security investigations.

---

## Work Performed

### 1. Verified Access and User State
- Logged into each server and confirmed root access.

<img src="https://github.com/user-attachments/assets/4e8f6f65-1769-44e9-a788-e361404c7cca" width="200"/>

- Verified that the user **mrice** existed on each host.
- Checked group membership to ensure proper privilege escalation.

<img width="1121" height="69" alt="image" src="https://github.com/user-attachments/assets/9940fb59-68a8-4d44-b6f2-4ec5a7cc71a1" />
Mrice user does NOT appear to be in the wheel group, which means I cannot disable root SSH yet; I would lose sudo access and that would lock me out.


### 2. Validated Sudo Privileges
- **dev‑app, dev‑performance, stage‑web:** Confirmed or added `mrice` to the `wheel` group.

<img src="https://github.com/user-attachments/assets/bbb53424-884f-40ae-a5ec-305e9229169a" width="250"/>

- **ansible server:** Verified sudo access through domain groups (no local `wheel` group required).

### 3. Ensured Safe SSH Testing
Confirmed the following setting on all servers to allow password-based testing:
PasswordAuthentication yes

<img src="https://github.com/user-attachments/assets/20d92516-6555-4a31-8617-85d658626ffb" width="250"/>


### 4. Tested User SSH Access
Successfully authenticated into each server as **mrice** to validate:
- SSH connectivity  
- Password authentication  
- Sudo functionality  

This ensured no lockout would occur after disabling root login.

<img src="https://github.com/user-attachments/assets/cbacfc73-371e-429e-836a-d5c571b482f8" width="250"/>


### 5. Disabled Root SSH Login
Updated SSH configuration on each server:
PermitRootLogin no



<img src="https://github.com/user-attachments/assets/3b15b004-cc13-4062-9068-b94a6a4235ab" width="200"/>




<img src="https://github.com/user-attachments/assets/e7e4d0f8-7a17-4713-8a0c-ea91161ccec6" width="100" />


Restarted SSH service:
systemctl restart sshd

<img src="https://github.com/user-attachments/assets/1939d66c-ae4e-4d5b-a49b-0cdad66a9730" width="200"/>


### 6. Verified Enforcement
Attempted SSH login as root on each server:
ssh root@<server-ip>

Confirmed:
- `Permission denied`
- Root login fully disabled

<img src="https://github.com/user-attachments/assets/0734b7e6-d4e6-49e6-8e67-655599f2e2a2" width="200"/>

---

## Issues Encountered & Resolutions

### dev‑performance
- Verified user existence and wheel membership before applying changes.

### stage‑web
- User already had correct sudo privileges; no adjustments required.

### ansible server
- No console access available.
- Verified sudo access via domain groups.
- Confirmed safe to disable root login without modifying local groups.

---

## Final State
- Root SSH login disabled on all servers.
- User **mrice** confirmed to have working SSH and sudo access everywhere.
- All systems hardened and compliant with secure access requirements.
- No lockouts or service interruptions occurred.


