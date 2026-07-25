# SSH Hardening – Restrict Access to Bastion Host Only (Ticket 25)

## Summary
Implemented SSH access restrictions across all servers to ensure that only the Bastion host can initiate SSH connections. This aligns with security department requirements and enforces a controlled, auditable access path. Verified connectivity, applied firewall rules, tested enforcement, and resolved host key issues encountered during configuration.

## Objective
Improve secure access practices by configuring SSH restrictions that allow connections exclusively from the Bastion host.

## Requirements
- **Systems:** All servers (application, performance, staging)
- **Task:** Allow SSH only from Bastion host; block all other sources

---

## Work Performed

### 1. Verified Server Identity and Access
For each server:
- Logged in as root  
- Confirmed correct system identity using:
whoami 
hostnamectl
- Verified IP address using:
ip a

### 2. Applied Firewall Restrictions
Configured each server to accept SSH only from the Bastion host by adding a rich rule:
firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="<bastion-ip>/32" port port="22" protocol="tcp" accept'

Removed default SSH access paths:
firewall-cmd --remove-port=22/tcp --permanent 
firewall-cmd --remove-service=ssh –permanent

Reloaded firewall:
firewall-cmd –reload

### 3. Testing Phase – SSH Access Validation

#### Test 1 — SSH from Bastion Host
Expected result: **SSH succeeds**
ssh <user>@<bastion-ip> 
ssh <user>@<server-ip>

#### Test 2 — SSH from Non‑Bastion Source (e.g., Windows)
Expected result: **Connection timed out**
ssh <user>@<server-ip>

Confirmed:
- Bastion → server = **working**
- Non‑Bastion → server = **blocked**

This validated that firewall restrictions were correctly applied.

---

## Host Key Issue Encountered & Resolution

One server produced a **remote host identification error** due to a rebuilt host key.  
Resolved using the following steps:

### 1. Regenerate SSH Keypair
ssh-keygen
Ensured fresh keypair and removed corrupted key files.

### 2. Re‑establish Trust with Server
ssh-copy-id <user>@<server-ip>
Installed the correct public key and restored passwordless SSH.

### 3. Update Known Hosts
ssh-keyscan -t ecdsa <server-ip> >> ~/.ssh/known_hosts
Manually added the new host fingerprint to ensure clean trust validation.

---

## Final Status
- SSH access is now **restricted exclusively to the Bastion host** on all servers.
- Non‑Bastion SSH attempts correctly fail with connection timeout.
- Bastion SSH access fully validated.
- Host key issues resolved and trust relationships restored.
- All systems hardened according to security department requirements.

## Tags
#linux #sysadmin #ssh #security #firewall #hardening #audit

<!-- Internal reference: Ticket #25 -->
