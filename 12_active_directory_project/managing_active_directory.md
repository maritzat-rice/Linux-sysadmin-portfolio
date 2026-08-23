# Managing Active Directory (Project Overview)

## Summary
Completed all required Active Directory management tasks as outlined in the wiki.  

Connected to the Windows Server via RDP and performed user, group, and password administration within the sandbox.prod → YellowTail OU.

## Work Performed
From the Windows Start Menu, searched for **Remote Desktop Connection**.

Entered the AD server address **10.X.XX.4**.

<img src="https://github.com/user-attachments/assets/ba03169c-3d1b-48bb-9073-29365ced72b1" width="250"/>


When prompted, entered the provided administrative credentials:
   - Username: **procore**
   - Password: **XXXXX**

<img src="https://github.com/user-attachments/assets/e10d1ae3-b87a-4460-8c57-e2a570f0b5ee" width="250"/>

Selected YES to connect anyway regardless of certificate errors

<img src="https://github.com/user-attachments/assets/276f2d6c-e36e-48f9-9ff8-6d21f033bb86" width="250"/>

Successfully connected to the Windows Server desktop environment.

Opened **Active Directory Users and Computers (ADUC)**.

From Active Directory Users and Computers, Navigated to sandbox.prod--> YellowTail

<img src="https://github.com/user-attachments/assets/9c8ce219-1a5b-4608-aa1a-37186288a633" width="250"/>

Selected New User

<img src="https://github.com/user-attachments/assets/564aeae0-ed1f-476a-8270-81e976c7e60d" width="250"/>

Filled in required user details and logon name

<img src="https://github.com/user-attachments/assets/0aa4f5e4-5d2b-494e-93ac-9ff1da81cb34" width="250"/>

Set the password and checked off option for user to change password at next logon, then Next

<img src="https://github.com/user-attachments/assets/1d2880f8-ec75-42e5-9495-cb98e9d91031" width="250"/>

Clicked finish

<img src="https://github.com/user-attachments/assets/905fdbf7-aac0-4046-a80d-23f399b50286" width="250"/>

================================================
### Next Created a Group

Selected New --> Group

<img src="https://github.com/user-attachments/assets/02e6b224-a322-4df5-ad08-5aaa2577ea58" width="250"/>

Entered Group name, then selected OK

<img src="https://github.com/user-attachments/assets/d8396a11-bd00-41b0-820c-833b1b36b0e1" width="250"/>

=====================================
### Next, reset user passwords
Right-clicked on user and selected Reset Password

<img src="https://github.com/user-attachments/assets/15577c64-fc8a-4807-9389-c40a0438aa61" width="300"/>

Entered new password
Unchecked user must change password at next logon


<img src="https://github.com/user-attachments/assets/3c3e1a41-1755-4d24-9dc4-f1ab7736c6eb" width="250"/>


<img src="https://github.com/user-attachments/assets/dfe6b97c-aac1-4c0b-8c87-e3d80d2fc49c" width="250"/>

Confirmed the password reset via the system message:
    *“The password for Maritza Rice has been changed.”*
Logged out of the server after confirming all changes were applied successfully.


## Screenshot Evidence
- Remote Desktop Connection window showing server connection.
- Windows Security credential prompt.
- Password reset confirmation dialog from Active Directory Domain Services.

## Status
All AD management tasks completed successfully. No issues encountered.



