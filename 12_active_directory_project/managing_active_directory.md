# Managing Active Directory (Project Overview)

## Summary
Completed all required Active Directory management tasks as outlined in the wiki.  

Connected to the Windows Server via RDP and performed user, group, and password administration within the sandbox.prod → YellowTail OU.

## Work Performed
From the Windows Start Menu, searched for **Remote Desktop Connection**.

Entered the AD server address **10.X.XX.4**.

<img width="338" height="212" alt="image" src="https://github.com/user-attachments/assets/ba03169c-3d1b-48bb-9073-29365ced72b1" />


When prompted, entered the provided administrative credentials:
   - Username: **procore**
   - Password: **XXXXX**

<img width="436" height="324" alt="image" src="https://github.com/user-attachments/assets/e10d1ae3-b87a-4460-8c57-e2a570f0b5ee" />

Selected YES to connect anyway regardless of certificate errors

<img width="384" height="404" alt="image" src="https://github.com/user-attachments/assets/276f2d6c-e36e-48f9-9ff8-6d21f033bb86" />

Successfully connected to the Windows Server desktop environment.

Opened **Active Directory Users and Computers (ADUC)**.

From Active Directory Users and Computers, Navigated to sandbox.prod--> YellowTail

<img width="967" height="540" alt="image" src="https://github.com/user-attachments/assets/9c8ce219-1a5b-4608-aa1a-37186288a633" />

Selected New User

<img width="743" height="582" alt="image" src="https://github.com/user-attachments/assets/564aeae0-ed1f-476a-8270-81e976c7e60d" />

Filled in required user details and logon name

<img width="432" height="375" alt="image" src="https://github.com/user-attachments/assets/0aa4f5e4-5d2b-494e-93ac-9ff1da81cb34" />

Set the password and checked off option for user to change password at next logon, then Next

<img width="431" height="374" alt="image" src="https://github.com/user-attachments/assets/1d2880f8-ec75-42e5-9495-cb98e9d91031" />

Clicked finish

<img width="430" height="374" alt="image" src="https://github.com/user-attachments/assets/905fdbf7-aac0-4046-a80d-23f399b50286" />

================================================
### Next Created a Group

Selected New --> Group

<img width="532" height="581" alt="image" src="https://github.com/user-attachments/assets/02e6b224-a322-4df5-ad08-5aaa2577ea58" />

Entered Group name, then selected OK

<img width="431" height="372" alt="image" src="https://github.com/user-attachments/assets/d8396a11-bd00-41b0-820c-833b1b36b0e1" />

=====================================
### Next, reset user passwords
Right-clicked on user and selected Reset Password

<img width="960" height="545" alt="image" src="https://github.com/user-attachments/assets/15577c64-fc8a-4807-9389-c40a0438aa61" />

Entered new password
Unchecked user must change password at next logon

<img width="372" height="258" alt="image" src="https://github.com/user-attachments/assets/3c3e1a41-1755-4d24-9dc4-f1ab7736c6eb" />

<img width="349" height="148" alt="image" src="https://github.com/user-attachments/assets/dfe6b97c-aac1-4c0b-8c87-e3d80d2fc49c" />

Confirmed the password reset via the system message:
    *“The password for Maritza Rice has been changed.”*
Logged out of the server after confirming all changes were applied successfully.


## Screenshot Evidence
- Remote Desktop Connection window showing server connection.
- Windows Security credential prompt.
- Password reset confirmation dialog from Active Directory Domain Services.

## Status
All AD management tasks completed successfully. No issues encountered.



