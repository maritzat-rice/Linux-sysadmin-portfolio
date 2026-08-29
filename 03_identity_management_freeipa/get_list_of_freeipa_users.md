## Get List of All FreeIPA Users & Delete Terminated User

## Objective
Generate a complete list of all FreeIPA users and remove a terminated user from the identity directory. This task demonstrates command‑line FreeIPA administration, identity lifecycle management, and compliance documentation.

## Summary
Logged into the dev-app-XX server and used FreeIPA CLI commands to retrieve all registered users. Redirected the output to a text file for HR review.  
Additionally, deleted the user **mpaxton**, who was previously created in Ticket #6 and later terminated.  
This completes the full IAM lifecycle: user creation → group assignment → user removal.

---

## Completed Tasks

### 🔹 1. Logged into Dev-App Server
SSH workflow:
- Bastion → dev-app-XX  
- Logged in as **mrice**


<img src="https://github.com/user-attachments/assets/4d103e17-4901-495d-bfff-7ca2a9c7ac02" width="250"/>



<img src="https://github.com/user-attachments/assets/3ff3c7ab-48fd-43cf-a510-3ae34b508cea" width="250"/>


Verified environment:
hostname
whoami


<img src="https://github.com/user-attachments/assets/8124b425-9231-43cd-a1c9-68d10994b1a8" width="200"/>


---

### 🔹 2. Generated List of All FreeIPA Users
Ran the FreeIPA command to list all users:
ipa user-find > /home/mrice/freeipa_users.txt


<img src="https://github.com/user-attachments/assets/fd19864e-2401-4ef2-bad2-2985197f8594" width="250"/>


Verified file contents:
cat /home/mrice/freeipa_users.txt


<img src="https://github.com/user-attachments/assets/0e5efc20-8926-435e-96e8-549f65049881" width="250"/>


**Output file:**  
`/home/mrice/freeipa_users.txt`


---

### 🔹 3. Deleted Terminated User (mpaxton)
HR requested removal of the user created in Ticket #6.

Command executed:
ipa user-del mpaxton


<img src="https://github.com/user-attachments/assets/b6c1e654-bcfd-4d95-9565-88097a139313" width="250"/>


Result:
- User **mpaxton** successfully deleted  
- Identity removed from FreeIPA directory

---

## Verification
- User list successfully generated and saved  
- File contains complete FreeIPA user listing  
- Terminated user **mpaxton** removed from directory  
- CLI commands executed successfully  
- IAM lifecycle completed

---

## Result
A full FreeIPA user listing was generated and stored for administrative review.  
The terminated user **mpaxton** was deleted using FreeIPA CLI, demonstrating command‑line identity management and compliance with HR offboarding requirements.
