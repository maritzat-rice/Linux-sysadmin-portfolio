# Network Setup Request — Static IP Configuration

## Objective
Strengthen networking fundamentals by configuring a static IP connection for a Linux server and validating internal/external connectivity, DNS resolution, and proper user/group configuration.

---

## Task Summary
Configure a static IP on the development application server, verify connectivity, create a local administrative user, assign proper group membership, and update the asset inventory system with required metadata.

---

## Requirements
- Configure static IP networking on the server  
- Apply correct gateway, netmask, and DNS settings  
- Create local user **XXX**  
- Assign password **XXXplus**  
- Add user to the **wheel** group  
- Update asset inventory with server details  
- Add hostname and IP information to documentation  

*(All sensitive IPs, hostnames, and organization names have been redacted.)*

---

## Steps Performed

### 1. Identify Assigned Static IP

- Used the IP Address Management (IPAM) sheet to locate the server’s assigned static IP address.

<img src="https://github.com/user-attachments/assets/033e01d3-e78b-4d13-b2d2-af0c1961dcd1" width="400"/>

---

### 2. Configure Static IP

- Applied static network settings using `nmcli`:

**nmcli con mod static ipv4.addresses "<redacted>" nmcli con mod static ipv4.gateway "<redacted>" nmcli con mod static ipv4.dns "<redacted>" nmcli con mod static ipv4.method manual nmcli con up static**

<img src="https://github.com/user-attachments/assets/abdc2857-0032-4ddc-aa05-0db5c1e9c4c5" width="250"/>

- After applying the new IP, the session disconnected as expected.  
- Reconnected using the updated network information.

<img src="https://github.com/user-attachments/assets/64db2bd9-f0e4-4bd8-9fc8-f9101390100a" width="250"/>

---

### 3. Verify Connectivity

<img src="https://github.com/user-attachments/assets/a362c915-a745-4f5d-b87a-08b6478ece22" width="250"/>

#### Internal Connectivity

- ping -c2 <redacted-gateway>

<img src="https://github.com/user-attachments/assets/a667dcef-df4f-4043-83af-52561934aad2" width="250"/>

#### External Connectivity

- ping -c2 google.com

<img src="https://github.com/user-attachments/assets/76d767ea-3920-48a3-bc93-b123ddf6e19f" width="250"/>

#### DNS Resolution

- getent hosts google.com

<img src="https://github.com/user-attachments/assets/92fc485e-922a-416a-9c57-60729fb6ae3d" width="250"/>

**Results:**  
- Static IP active  
- Gateway reachable  
- DNS server responding  
- DNS resolution successful  

---

## 4. Create Local User

### Create user

- sudo useradd -m XXX

<img src="https://github.com/user-attachments/assets/dd13c0a7-d8bf-455e-a6b9-4def4d549db7" width="250"/>

### Set password
sudo passwd XXX

<img src="https://github.com/user-attachments/assets/f99feefd-e337-444f-9247-688c19e69fbc" width="250"/>

### Add user to wheel group
sudo usermod -aG wheel XXX

<img src="https://github.com/user-attachments/assets/cf5d514c-6647-4054-a42a-19739a15d936" width="250"/>

### Verify group membership
id XXX

**User successfully added and granted administrative privileges.**

---

## 5. Asset Inventory Update

Updated the asset inventory system with the following redacted fields:

- **Asset Tag ID:** MRice-Ticket 4
- **Server Name:** dev-app-mr1.XXX.prod1  
- **Serial Number:** f095ce46-XXXX-XXXX-XXXX-05bb55ea0ebd
- **Description:** dev-app-mr1.XXXX.prod1  
- **Owner:** IT – Maritza  
- **Organization:** XXX  
- **IP:** 10.X.XX.172  
- **MAC:** 00:50:56:XX:XX:XX  
- **CPU:** 1 CPU  
- **Memory:** 1 GB  
- **Operating System:** Linux (64 bit)

<p>
<img src="https://github.com/user-attachments/assets/6ba19f53-25d0-4ae8-bf75-59d39233ff56" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/e4ae3e17-0c31-46a6-bc24-1263b1b13b76" width="250"/>
<p>

*All sensitive identifiers have been removed for public display.*

---

## Summary of Work Completed
- Configured static IP networking on the development server  
- Verified internal/external connectivity and DNS resolution  
- Created local user **XXX** and assigned administrative privileges  
- Updated asset inventory with required metadata  
- Documented hostname, IP, and configuration steps  

**Static networking configuration completed successfully.**
