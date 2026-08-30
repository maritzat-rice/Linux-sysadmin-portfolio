## Install & Configure FreeIPA Client

## Objective
Integrate a Linux server into a centralized identity management system using FreeIPA.  
This task demonstrates real-world IAM skills including host enrollment, Kerberos authentication, SSSD configuration, and troubleshooting domain join failures.

## Summary
Attempted to install and enroll the FreeIPA client on the **dev-app-XX** server.  
Encountered multiple issues including hostname validation errors and Kerberos credential failures during enrollment.  
Resolved these by correcting the system hostname and authenticating with the correct delegated user account.  
Successfully enrolled the host into the **XX.DEV** realm, enabling centralized authentication and identity management.

---
## Completed Tasks

### 🔹 1. Verified Network Reachability

- Checked connectivity to the FreeIPA server: ping -c2 10.1.XX.XXX

<img src="https://github.com/user-attachments/assets/355ef7d7-a1e6-486e-8475-3c0e7021ad75" width="250"/>


### 🔹 2. Installed FreeIPA Client Package: sudo yum install ipa-client -y

<img src="https://github.com/user-attachments/assets/b3fcbea7-7c1e-4b74-a7c2-392b87ca09fb" width="250"/>

### 🔹 3. Resolved Hostname Error

- **Initial error:** Invalid hostname, 'localhost' must not be used. 
- The ipa-client-install command failed.


**Fix:** Updated hostname to a valid FQDN.
- sudo hostnamectl set-hostname dev-app-XX.XX.dev 
- exec bash 
- hostname 
- hostnamectl


<img src="https://github.com/user-attachments/assets/3206a7e5-3a97-4bf2-852f-3dedb10275b2" width="300"/>

### 🔹 4. Ran Client Installation

- sudo ipa-client-install –mkhomedir

<img src="https://github.com/user-attachments/assets/6db20dce-9ace-49bb-97cc-76e990137e01" width="300"/>


## Troubleshooting & Root Cause Analysis

### 🔹 Issue: Kerberos Authentication Failure
During enrollment, received:
Password incorrect while getting initial credentials


### 🔹 Root Cause
Initially attempted enrollment using: admin@XX.DEV

However, in this environment, **host enrollment permissions were delegated to individual user accounts**, not the global admin.

My personal FreeIPA user (**mrice**) was:

- Enabled  
- Assigned a UID  
- Fully provisioned  
- Granted host enrollment permissions  

This meant the admin password was rejected, but my user credentials were valid.

---

### 🔹 How the Issue Was Identified
Checked the FreeIPA UI:

- User appeared under *User Login → mrice*  
- Status: Enabled  
- UID assigned  
- Account active and provisioned  

This confirmed my user had the correct permissions.

---

### 🔹 Resolution
Reran the installer using:
User authorized to enroll computers: mrice 
Password: <XX onboarding password>


Kerberos authenticated successfully, and enrollment completed without errors.

<img src="https://github.com/user-attachments/assets/cf045c9f-c6b3-432e-a455-27331c699dfd" width="300"/>

## Outcome
The FreeIPA client installation succeeded, and the system is now properly enrolled in the **XX.DEV** realm.

The following components were configured automatically:

- **SSSD**  
- **Kerberos**  
- **mkhomedir**  
- **Domain enrollment**  
- **Centralized authentication**

This completes the integration of the Linux server into the FreeIPA identity management environment.

---

## Result
FreeIPA client installation and domain enrollment completed successfully.  
Host is now managed under centralized identity policies, enabling secure authentication and access control across the environment.


