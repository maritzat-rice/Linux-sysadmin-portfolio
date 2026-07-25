# SSH Hardening – Disable Root Login (Ticket 24)

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
- Verified that the user **mrice** existed on each host.
- Checked group membership to ensure proper privilege escalation.

### 2. Validated Sudo Privileges
- **dev‑app, dev‑performance, stage‑web:** Confirmed or added `mrice` to the `wheel` group.
- **ansible server:** Verified sudo access through domain groups (no local `wheel` group required).

### 3. Ensured Safe SSH Testing
Confirmed the following setting on all servers to allow password-based testing:
PasswordAuthentication yes

### 4. Tested User SSH Access
Successfully authenticated into each server as **mrice** to validate:
- SSH connectivity  
- Password authentication  
- Sudo functionality  

This ensured no lockout would occur after disabling root login.

### 5. Disabled Root SSH Login
Updated SSH configuration on each server:
PermitRootLogin no

Restarted SSH service:
systemctl restart sshd

### 6. Verified Enforcement
Attempted SSH login as root on each server:
ssh root@<server-ip>

Confirmed:
- `Permission denied`
- Root login fully disabled

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

## Tags
#linux #sysadmin #ssh #security #hardening #sudo #audit

<!-- Internal reference: Ticket #24 -->
