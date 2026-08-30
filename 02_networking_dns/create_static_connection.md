# Static Connection Configuration — stage-web Server

## Objective
Strengthen networking fundamentals by configuring a static IP connection for a Linux server and validating internal/external connectivity, DNS resolution, and proper user/group configuration.

---

## Task Summary
Create a static network connection for the staging web server using information from the IP Address Management (IPAM) sheet. Validate connectivity, configure a local administrative user, assign proper group membership, and update the asset inventory system.

---

## Requirements
- Configure static IP networking on the server  
- Apply correct gateway, netmask, and DNS settings  
- Create local user **XXX**  
- Assign password **XXXplus**  
- Add user to the **wheel** group  
- Update asset inventory with server details  

*(All sensitive IPs, hostnames, and organization names have been redacted.)*

---

## Steps Performed

### 1. Identify Assigned Static IP

**Used the IP Address Management (IPAM) sheet to locate the server’s assigned static IP address.**

<img src="https://github.com/user-attachments/assets/9cc3ebb0-80f8-4655-9970-8eed2cfc5f41" width="400"/>

---

### 2. Configure Static IP

**Applied static network settings using `nmcli`:**

- nmcli con add con-name static \ ifname ens192 \ type ethernet \ autoconnect yes \ ip4 "<redacted-ip>/<redacted-netmask>" \ gw4 "<redacted-gateway>" \ ipv4.dns "<redacted-dns>"

<img src="https://github.com/user-attachments/assets/8739adbd-692e-4dab-8b12-8ee16030b6b1" width="250"/>


**Brought the connection online:**

- nmcli con up static

<img src="https://github.com/user-attachments/assets/69deb22e-52aa-4b9f-a5d1-b0db85975f65" width="250"/>

---

### 3. Verify Connectivity

#### Internal Connectivity

-ping -c2 <redacted-gateway>

<img src="https://github.com/user-attachments/assets/d3e5ecf1-6946-4194-82ea-fa261fc82217" width="200"/>

#### External Connectivity

-ping -c2 google.com

<img src="https://github.com/user-attachments/assets/ef7f3fe1-eca9-480d-b696-490a8e6d4c34" width="250"/>

#### DNS Resolution

-getent hosts google.com

<img src="https://github.com/user-attachments/assets/59d9658a-2a37-46c3-ba37-9d6b3c6d4c4e" width="250"/>


**Results:**  
- Static IP active  
- Gateway reachable  
- DNS server responding  
- DNS resolution successful  

---

## 4. Create Local User

### Create user

-sudo useradd -m XXX

<img src="https://github.com/user-attachments/assets/2a366039-d625-47ce-89a6-91cf18693e46" width="200"/>

### Set password

-echo XXXXplus | sudo passwd --stdin XXX

<img src="https://github.com/user-attachments/assets/2508863b-d0b1-4795-96f9-ecdc8c0eb384" width="250"/>

### Add user to wheel group

-sudo usermod -aG wheel XXX

<img src="https://github.com/user-attachments/assets/022091df-5fb9-40a3-9530-c3fd12b49e93" width="250"/>

### Verify group membership
-id XXXX

*User successfully added and granted administrative privileges.*

---

## 5. Asset Inventory Update

**Updated the asset inventory system with the following redacted fields:**

- **Asset Tag ID:** MRice-Ticket 22  
- **Server Name:** stage-web-mr1.XXX.prod1  
- **Serial Number:** f095ce46-XXX-XXX-XXX-05bb55ea0ebd  
- **Description:** Create a Static Connection  
- **Owner:** Maritza  
- **Organization:** <redacted>  
- **IP:** 10.X.XX.176  
- **MAC:** 00:XX:XX:XX:a6:2f  
- **CPU:** 1 vCPU  
- **Memory:** 1 GB  
- **Operating System:** Linux (64 bit)  
- **Status:** Active  

*All sensitive identifiers have been removed for public display.*

<p>
<img src="https://github.com/user-attachments/assets/e142ca83-8a70-4b4a-b36f-1b556afa42c3" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/38015143-6af1-43f3-9afe-0e99dc8dc091" width="250"/>
<p>

---

## Summary of Work Completed
- Configured static IP networking on the staging web server  
- Verified internal/external connectivity and DNS resolution  
- Created local user **XXX** and assigned administrative privileges  
- Updated asset inventory with required metadata  
- Documented hostname, IP, and configuration steps  

**Static networking configuration completed successfully.**





