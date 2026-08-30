## Applying Apache to a Firewall

## Objective
Open required Apache ports (80 and 443) and allow Apache services through the firewall on the stage‑web‑mr1 server. This task builds practical web server administration skills by configuring and tuning Apache services securely.

## Summary
Completed Apache firewall configuration on **stage‑web‑mr1**.  
After elevating to root, both HTTP (80/tcp) and HTTPS (443/tcp) ports were added to the permanent firewall rules. Apache services (http and https) were enabled, the firewall was reloaded, and the configuration was verified using `firewall-cmd --list-all`. All required ports and services were successfully applied, ensuring Apache traffic is fully allowed through the firewall.

## Completed Tasks
- Connected to **stage‑web‑mr1** via Bastion and elevated to root.
- Added required Apache ports:

<p>
<img src="https://github.com/user-attachments/assets/74a06159-3545-48e8-8bb2-6570b09ce692" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/0382cb4e-d7f2-4c91-986a-a6b6995a526c" width="250"/>
<p>

- Allowed Apache services:


<img src="https://github.com/user-attachments/assets/f0c8146a-6fd6-4724-bf2c-76abfe045ba6" width="250"/>


- Reloaded the firewall:


<img src="https://github.com/user-attachments/assets/18af313f-91cc-4d92-8eb4-96d216a410ea" width="250"/>


- Verified configuration:


<img src="https://github.com/user-attachments/assets/99a7d1f9-16c8-46bd-b8c5-1d57be3f0482" width="250"/>


## Result
Apache traffic is now fully allowed through the firewall, meeting all ticket requirements.
