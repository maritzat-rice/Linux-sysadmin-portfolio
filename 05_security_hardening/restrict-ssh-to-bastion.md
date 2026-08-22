# SSH Hardening – Restrict Access to Bastion Host Only 

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

<img width="238" height="105" alt="image" src="https://github.com/user-attachments/assets/cf6dd12d-4606-4d49-adfd-34f5a139f9e4" />

<img width="626" height="179" alt="image" src="https://github.com/user-attachments/assets/6e475ac2-f4b0-46cc-a3a4-cde886ca5102" />



### 2. Applied Firewall Restrictions
Configured each server to accept SSH only from the Bastion host by adding a rich rule:
firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="<bastion-ip>/32" port port="22" protocol="tcp" accept'

<img width="1051" height="64" alt="image" src="https://github.com/user-attachments/assets/d7e9c116-f5ac-42b5-adae-6e29d16d65b7" />

Removed default SSH access paths:
firewall-cmd --remove-port=22/tcp --permanent 
firewall-cmd --remove-service=ssh –permanent

<img width="493" height="102" alt="image" src="https://github.com/user-attachments/assets/00d29f7e-c591-4c7c-a214-8f9b60db2fcb" />


Reloaded firewall:
firewall-cmd –reload

<img width="332" height="63" alt="image" src="https://github.com/user-attachments/assets/d26191be-d54c-46e3-a91f-6cb3ef4a5b4c" />


### 3. Testing Phase – SSH Access Validation

#### Test 1 — SSH from Bastion Host
Expected result: **SSH succeeds**
ssh <user>@<bastion-ip> 
ssh <user>@<server-ip>

<img width="727" height="184" alt="image" src="https://github.com/user-attachments/assets/df91dd95-37dd-4268-841f-6969d1e5b72e" />


#### Test 2 — SSH from Non‑Bastion Source (e.g., Windows)
Expected result: **Connection timed out**
ssh <user>@<server-ip>


<img width="576" height="86" alt="image" src="https://github.com/user-attachments/assets/8acc356d-8e37-4726-92e5-f406df0000e6" />


Confirmed:
- Bastion → server = **working**
- Non‑Bastion → server = **blocked**

This validated that firewall restrictions were correctly applied.

---

## Host Key Issue Encountered & Resolution

One server produced a **remote host identification error** due to a rebuilt host key.  

### Issue : remote host identification on server 10.X.XX.176


Resolved using the following steps:

### 1. Regenerate SSH Keypair
Ran command: ssh-keygen

- regenerated your SSH keypair
- ensured your public key existed
- cleaned up any missing or corrupted key files

Ensured fresh keypair and removed corrupted key files.

### 2. Re‑establish Trust with Server
Ran command: ssh-copy-id mrice@<server-ip>

- connects to the remote server
- installs your public key into its ~/.ssh/authorized_keys
- ensures passwordless SSH works
- forces a fresh trust relationship

Installed the correct public key and restored passwordless SSH.

### 3. Update Known Hosts
ssh-keyscan -t ecdsa <server-ip> >> ~/.ssh/known_hosts

- This command manually added the new host fingerprint to my known_hosts file.

Manually added the new host fingerprint to ensure clean trust validation.

---

## Final Status
- SSH access is now **restricted exclusively to the Bastion host** on all servers.
- Non‑Bastion SSH attempts correctly fail with connection timeout.
- Bastion SSH access fully validated.
- Host key issues resolved and trust relationships restored.
- All systems hardened according to security department requirements.


