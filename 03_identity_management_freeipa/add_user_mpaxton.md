## Add User "mpaxton" to FreeIPA

## Objective
Create a new FreeIPA user account for a recently onboarded developer and assign the user to the **webmasters** group. This task demonstrates centralized identity management, user provisioning, group membership assignment, and password setup within FreeIPA.

## Summary
Logged into the FreeIPA UI and created a new user account for **Martina Paxton (mpaxton)**.  
Configured the user’s profile, set a temporary password, and added the user to the **webmasters** group.  
Verified group membership to ensure proper access control and identity propagation.

---

## Completed Tasks

### 🔹 1. Logged into FreeIPA Web UI
Accessed the FreeIPA console at:  https://ipa.XX.dev/ipa/ui

---

### 🔹 2. Created New User Account
Navigation:
- **Identity → Users → Add**

Entered user details:
- **User Login:** mpaxton  
- **First Name:** Martina  
- **Last Name:** Paxton  
- **Class:** (blank)  
- **No Private Group:** unchecked  
- **GID:** (blank)  
- **New Password:** TempPass1234  
- **Verify Password:** TempPass1234  

Clicked **Add and Edit** to open the user profile page.


<img src="https://github.com/user-attachments/assets/06e4eca5-f0ef-48f0-a072-cea9a5e50f15" width="300"/>


---

### 🔹 3. Added User to "webmasters" Group
Navigation:
- User Profile → **User Groups** tab  
- Click **Add**

Actions:
- Selected **webmasters** from the Available Groups list  
- Moved it to **Prospective** using the “>” button  
- Clicked **Add** to finalize

<img src="https://github.com/user-attachments/assets/a2b694d8-b9f1-40ff-8954-3aa0cd65b33f" width="300"/>


<img src="https://github.com/user-attachments/assets/000723f2-773a-4a3c-9b0b-0364c7f3ad3a" width="300"/>


<img src="https://github.com/user-attachments/assets/d6a2b076-c92d-472a-821c-0c252bee501f" width="300"/>


---

### 🔹 4. Verified Group Membership
Returned to the user profile page and confirmed:

**Direct Membership:**  
- webmasters ✔

This confirms the user was successfully added to the correct group.


<img src="https://github.com/user-attachments/assets/d3d91d79-e1b0-4b26-a19c-18c491562505" width="300"/>


---

## Verification
- User account created successfully  
- Temporary password set  
- Group membership assigned  
- Identity visible under FreeIPA Users  
- Group propagation confirmed under Direct Membership  

---

## Result
The new developer account **mpaxton** has been successfully created and added to the **webmasters** group.  
This ensures proper access control and centralized identity management within the FreeIPA environment.
