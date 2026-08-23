# DNS Resolution Update – Adding Local Hostname Entries

## Summary
Hostname resolution was failing for several internal systems on a development server. To restore proper resolution, the required DNS entries were added to the local `/etc/hosts` file as part of a configuration update.

## Requirements
**System:** Development application server  
**DNS Entries Provided:**  
Multiple internal hostname-to-IP mappings were supplied by the team (redacted for security). These entries were required for internal communication between services and monitoring tools.


## Actions Taken
- Connected to the server via SSH for clean copy/paste and command execution.
- Verified logged-in user using: whoami

<img src="https://github.com/user-attachments/assets/96f6274c-3b7b-470e-925f-00a1f7b7cb31" width="150"/>

- Opened the system hosts file: sudo vi /etc/hosts

<img src="https://github.com/user-attachments/assets/0087ddcc-53de-4aaa-8904-47674ca19abf" width="250"/>

- Added all required hostname-to-IP mappings (internal values redacted).

<img src="https://github.com/user-attachments/assets/301da1dc-0282-4f76-9cce-187963141f7b" width="250"/>

- Saved and exited the file.

<img src="https://github.com/user-attachments/assets/754e05a2-b078-4fc9-bcd8-227908856122" width="250"/>


## Validation
- Verified hostname resolution using: getent hosts <hostname>

<img src="https://github.com/user-attachments/assets/b9c6944a-06fc-46ec-ab0d-0bcd4dce729f" width="250"/>

- Confirmed successful resolution with: ping -c 3 <hostname>

<img src="https://github.com/user-attachments/assets/e7753267-7a71-46d0-82ec-e0c19c75b610" width="250"/>


## Result
All DNS entries were added successfully. Hostname resolution on the server is functioning as expected.



