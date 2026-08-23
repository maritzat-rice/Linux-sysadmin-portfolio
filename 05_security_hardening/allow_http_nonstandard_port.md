## Allow HTTP on Non‑Standard Port (8001)

## Objective
Configure the dev‑performance web server to listen on a non‑standard HTTP port (8001) while maintaining proper SELinux, Apache, and firewall configurations. This task builds practical networking and Linux troubleshooting skills.

## Summary
The network and security teams requested that the dev‑performance server accept HTTP traffic on port **8001** instead of the default port 80. SELinux initially blocked the port, and Apache was not installed, resulting in an empty `httpd.conf`. After installing Apache, updating SELinux policies, configuring the Apache listener, and opening the port in firewalld, the server successfully served the Apache test page on port 8001 using both hostname and IP.

## Completed Tasks
- Installed SELinux management utilities:  
(Command: dnf install -y policycoreutils-python-utils)


<img src="https://github.com/user-attachments/assets/496635bd-0222-490a-bc54-ca33962475a7" width="350"/>


- Added port **8001** to SELinux `http_port_t`:
(Used man semanage port to get the syntax: semanage port -a -t http_port_t -p tcp 8001)

<img src="https://github.com/user-attachments/assets/c39fabc8-2142-4e77-abf7-3020408e4f27" width="250"/>

- To verify port is added correctly ran: semanage port -l | grep 8001

<img src="https://github.com/user-attachments/assets/9a8f3e0b-ce0e-4390-aa23-3dd60bc73729" width="250"/>


- Identified issue: `httpd.conf` was blank because Apache was not installed.
- Installed Apache to resolve missing configuration.
- Updated Apache configuration by adding: Listen 8001
  (command: vi /etc/httpd/conf/httpd.conf)

<img src="https://github.com/user-attachments/assets/2fa77245-5356-4052-9fd3-85a6b7d82cab" width="150"/>

- Apache was not installed yet; verified not installed by running "rpm -q httpd"

<img src="https://github.com/user-attachments/assets/de5ccf71-714d-4a8e-a385-63a99b416009" width="300"/>

### Ran the following commands:

<img src="https://github.com/user-attachments/assets/ca3a8f1d-5a91-43e1-b11d-bfa8ab46c434" width="350"/>


- Confirmed it is active and running
- Also checked listening ports with command: ss -tulnp | grep httpd


<img src="https://github.com/user-attachments/assets/98c7e8e7-f3af-45e8-a0c8-bae64d520805" width="350"/>


## Next Steps: Open Port 8001 in Firewalld

<img src="https://github.com/user-attachments/assets/5321d8ea-e46c-4ac0-a34e-230ebbad76fa" width="350"/>


### Outcome: All configurations applied cleanly. SELinux, Apache, and firewalld are aligned and functioning as expected.




