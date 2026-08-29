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

===================================================================
## Additional Access Assignment: Add User to "support" Group

### Objective
Assign the newly created user **mpaxton** to the **support** group to grant access required for the production webpage revamp project.

### Steps Completed

1.	Logged into the FreeIPA UI:  https://ipa.XX.dev/ipa/ui

2. Navigated to:
- **Identity → Users**
- Searched for: **mpaxton**
- Clicked the username to open the profile

3. Selected the **User Groups** tab to view current memberships:
- ipausers  
- webmasters  


<img src="https://github.com/user-attachments/assets/12026ede-e3cc-478e-978e-183d74601c15" width="300"/>

4. Clicked **Add** to open the group selection dialog.

5. In the Available Groups list:
- Checked **support**
- Clicked the **>** arrow to move it into the Prospective panel


<img src="https://github.com/user-attachments/assets/5c251696-eac6-40fd-aa33-d36f0ff68f14" width="300"/>

6. Clicked **Add** to finalize the group assignment.

<img src="https://github.com/user-attachments/assets/66cf3f7e-ce09-4c0c-af77-b70124e7f750" width="300"/>


### Verification
Returned to the user profile and confirmed:

**Direct Membership:**
- webmasters  
- support ✔

This confirms the user was successfully added to the **support** group.


<img src="https://github.com/user-attachments/assets/c4ea8b0e-7779-4b4a-8dab-491db2c24f84" width="300"/>


