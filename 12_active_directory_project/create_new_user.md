## Task Overview
The objective of this ticket was to create a new Active Directory user within the **mrice‑VITI** Organizational Unit (OU). The user needed to be named **Curtis Rice**, assigned the username **crice**, placed in the correct OU, and configured with the password **XXXXXXXX!** with **Password never expires** enabled.

## Actions Performed
- Opened **Active Directory Users and Computers (ADUC)** and navigated to **VITI → mrice‑VITI**.

<img width="734" height="540" alt="image" src="https://github.com/user-attachments/assets/b7f58ded-92d2-4333-898a-12eeb1be69f8" />

- Launched the **New User** wizard and entered the required user details:
  - First Name: Curtis  
  - Last Name: Rice  
  - Username: crice

<img width="432" height="376" alt="image" src="https://github.com/user-attachments/assets/a5c25bb1-2058-42e4-a44a-974bd04b39f9" />

- Set the password to **XXXXXXXX!**.
- Enabled **Password never expires**.

<img width="433" height="375" alt="image" src="https://github.com/user-attachments/assets/e21cbd79-dcc8-4c0a-8401-9f3f934660b5" />

- Ensured **User must change password at next logon** remained **unchecked**, per ticket requirements.

<img width="435" height="371" alt="image" src="https://github.com/user-attachments/assets/5a23beac-a4ea-4114-a2a6-e4f430ff5f09" />





## Verification
- Confirmed the new user object **crice** appears under the correct OU (**mrice‑VITI**).
- Verified that the password settings match the ticket requirements.

<img width="469" height="537" alt="image" src="https://github.com/user-attachments/assets/ff4d5008-4955-4e43-9668-d1ac12006a85" />

## Attachments
- Screenshot of the New User creation wizard.
- Screenshot of password settings.
- Screenshot of the final user object inside the **mrice‑VITI** OU.

## Status
User creation completed successfully. No issues encountered.
