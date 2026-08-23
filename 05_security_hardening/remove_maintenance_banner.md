## Remove Maintenance Banner

## Objective
Restore the dev‑performance website by removing the maintenance banner and redeploying the “Up and Ready” version of the site. This task reinforces controlled code deployment and maintaining service availability during updates.

## Summary
Completed the removal of the maintenance banner on the **dev‑performance** server.  
After connecting as mrice, the correct “Up and Ready” version of the website was located in the `websiteUpAndReady/` directory of the procore-products repository. These files were copied into `/var/www/html` to replace the maintenance version. Apache was restarted, and verification confirmed that the live site now displays the “Website is up and running” banner with no remaining maintenance messaging.

## Completed Tasks
- Connected to **dev-performance** as `mrice`.
- Navigated to: /var/www/html/procore-products/websiteUpAndReady
- Verified the correct “Up and Ready” version of the website.
- Copied updated site files into Apache’s DocumentRoot: /var/www/html
replacing the maintenance banner.
- Restarted Apache to apply changes:systemctl restart httpd
- Verified the live site at:
- http://10.1.30.175/procore-products/procore  
- http://dev-performance-mr1.procore.prod1/procore  
Displays the **“Website is up and running”** banner.
- Confirmed no maintenance messaging remains on the active application.

## Verification
- Browser shows the correct “Up and Ready” banner.
- Apache restarted successfully with no errors.
- DocumentRoot contains the correct production `index.html`.
- Maintenance banner fully removed.

## Result
Website successfully restored.  
Maintenance banner removed.  
Service remains fully operational.

## Attachments

### WebsiteUpAndReady Directory

<img src="https://github.com/user-attachments/assets/99118074-7fd9-43c3-a6d2-53ad2d4c2ddb" width="350"/>



<img src="https://github.com/user-attachments/assets/d784b659-eb90-4660-820a-4702701246ac" width="250"/>

### File Copy to /var/www/html


<img src="https://github.com/user-attachments/assets/a4410cde-258d-491e-bc96-1d6978e22776" width="250"/>

### Apache Restart Confirmation


<img src="https://github.com/user-attachments/assets/852a8444-fc15-4e67-8900-88130fe760df" width="250"/>


### “Website is up and running” Banner


<img src="https://github.com/user-attachments/assets/a01e930f-d374-4d4f-8681-aa367c28ac01" width="250"/>



