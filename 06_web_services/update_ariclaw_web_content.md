## Update Apache Web Content (Ariclaw Contact Page)

## Objective
Update the Ariclaw website contact information on **stage-web-mr1.XX.prod1** by modifying the NFS‑hosted HTML file and deploying the updated content to Apache’s web root.

## Summary
Verified the updated phone number in the NFS share, copied the updated contact page into Apache’s web root, corrected ownership, and confirmed the change is live in the browser.

---

## Completed Tasks

### 🔹 1. Connected to Stage-Web Server

**From bastion:**

- ssh mrice@10.X.XX.176

**Verified:**

- whoami 
- hostname

<img src="https://github.com/user-attachments/assets/503dabb1-ba0a-4192-9f67-46f443e38b54" width="150"/>

---

## Validate Updated Contact Page

### 🔹 2. Checked Existing Phone Number in NFS Share

**grep -n "800" /nfs/incoming/vhosts/ariclaw/htdocs/contact.html**

<img src="https://github.com/user-attachments/assets/cb7487ba-61ea-4f19-b3d8-b6f862b2456a" width="350"/>

**Output confirmed the updated number:**
00 (800) 9865 562


*No edits required — file already contained the correct phone number.*

---

## Deploy Updated Content to Apache

### 🔹 3. Copied Updated Contact Page to Web Root

- sudo cp /nfs/incoming/vhosts/ariclaw/htdocs/contact.html /var/www/html/

<img src="https://github.com/user-attachments/assets/4af49de4-8e2a-4c50-b23f-aba57662beff" width="350"/>

### 🔹 4. Fixed Ownership

- sudo chown apache:apache /var/www/html/contact.html

<img src="https://github.com/user-attachments/assets/f197f1fe-a812-4d2b-94b5-9de1bd19cc73" width="350"/>

Apache must own the web root for proper access.

---

## Functional Verification

### 🔹 5. Tested in Browser

**Opened:**

- http://10.X.XX.176/contact.html (10.X.XX.176 in Bing)

**Result:**
- Updated phone number displayed correctly  
- Ariclaw website serving updated content from **stage-web-mr1.XX.prod1**

<img src="https://github.com/user-attachments/assets/f55b7937-cd0c-4eea-aeba-ce5e5fd1d11f" width="350"/>

---

## Result
The Ariclaw contact page was successfully updated and deployed to Apache’s web root.  
The new phone number **00 (800) 9865 562** is now live and visible on the staging web server.



