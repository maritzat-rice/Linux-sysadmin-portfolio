## Notify Website Under Maintenance

## Objective
Deploy a maintenance banner to the dev‑performance web server while maintaining service availability during code changes. This task reinforces practical web server administration and controlled code deployment skills.

## Summary
Completed deployment of the maintenance banner on **dev‑performance**.  
After connecting to the server and escalating to root, the procore-products repository was cloned into `/var/www/html` using HTTPS due to missing SSH keys. The maintenance version located in `websiteDownForMaintenance/` was identified, and the active site’s `index.html` was replaced with the maintenance banner. Apache was restarted, and verification confirmed the banner displayed correctly in the browser.

## Completed Tasks
- Connected to:dev-performance-XX1.XXXXXXX.prod1 as **mrice**, then escalated to root.

<p>
<img src="https://github.com/user-attachments/assets/a1ae78a2-bd1b-4b23-807e-63a03300b810" width="225"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ea69cb18-fb27-43c6-a667-cba3ff989617" width="250"/>
<p>


- **Cloned the repository into Apache’s DocumentRoot using HTTPS:**

<p>
<img src="https://github.com/user-attachments/assets/6596f8d9-634a-4a0d-ad0c-1519edfa66ee" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/7cd60e4d-9639-4688-bd3b-8b68e4978ba6" width="350"/>
<p>


- Located the maintenance version in: `websiteDownForMaintenance/` 
- Replaced the active site’s `index.html` with the maintenance banner by placing it directly in:/var/www/html/ **(required by Apache’s default DocumentRoot)**
- Restarted Apache to apply changes:**systemctl restart httpd**
- Verified in browser that the maintenance banner is live:
- http://10.X.XX.175  
- http://dev-XXXXX.XXXXX.prod1

## Issues Encountered & Resolutions
- **SSH clone failed** due to missing SSH keypair on the VM  
→ Switched to **HTTPS clone**, which succeeded.
- Apache initially served the **CentOS test page**


<img src="https://github.com/user-attachments/assets/dc66b2ed-83d2-4469-8523-2c2ec73de87a" width="250"/>


→ Resolved by placing the maintenance `index.html` directly in `/var/www/html` instead of inside the repo subdirectory.


<img src="https://github.com/user-attachments/assets/fa172e20-cbf4-4c43-9457-5a4ec7896386" width="400"/>




<img src="https://github.com/user-attachments/assets/cf206f83-8e21-4362-99dd-535cb8b4d1ef" width="400"/>




## Verification
- Browser displays the maintenance banner correctly.


<img src="https://github.com/user-attachments/assets/c7afbe5c-9ee1-499f-b19b-c9af56ca574e" width="250"/>

- Apache service restarted without errors.

<img src="https://github.com/user-attachments/assets/e3c89147-7489-4c4c-8548-1707c7a31817" width="250"/>

- DocumentRoot contains the correct maintenance `index.html`.

<img src="https://github.com/user-attachments/assets/aa55140f-dc2e-4d31-b013-3ae0c8c00603" width="400"/>


## Result
Maintenance banner is fully deployed and visible.  
Ticket completed successfully.






