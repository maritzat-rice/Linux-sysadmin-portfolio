## Update System Inventory Database Using Git + host_facts.sh

## Objective
Populate the system inventory database for **dev-app-mr1.XX.prod1** and **dev-performance-mr1.XX.prod1** by downloading the scripts repository and running the `host_facts.sh` script. This task demonstrates Git usage, script execution, and inventory data collection.

## Summary
Installed Git on both servers, cloned the scripts repository, executed the `host_facts.sh_DoNotDelete` script, and verified that inventory files were generated under `/tmp` on each server.

---

## Completed Tasks

### 🔹 1. Installed Git on Both Servers

On **dev-app**:

<img src="https://github.com/user-attachments/assets/d10a01a3-e204-4e79-b13f-0b867d84fae4" width="250"/>


- sudo dnf install -y git

On **dev-app**

<img src="https://github.com/user-attachments/assets/1faa76c8-7423-4083-ae43-c0682dd9cc59" width="250"/>

## Git installed successfully on both nodes.

---

# 🟦 Clone Scripts Repository

### 🔹 2. Cloned Repository on Each Server

- cd ~ 
- git clone https://gitlab.com/procoreplusmd/scripts.git

<p>
<img src="https://github.com/user-attachments/assets/88ea5dff-7e7f-4e2d-aa82-13657ea197d2" width="200"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/81987911-c21c-44c2-9d51-7c906accbae9" width="300"/>
<p>


On **dev-app**:

- Repository already existed  

<img src="https://github.com/user-attachments/assets/9aeec173-cd99-488c-8859-c29643973dd1" width="300"/>

## Verified with:

- ls -ld ~/scripts

<img src="https://github.com/user-attachments/assets/7fadf54a-9353-4bd3-b333-ca1796f4c9b6" width="300"/>

---

# 🟦 Run Inventory Script

### 🔹 3. Navigated Into Scripts Directory

- cd ~/scripts 

<img src="https://github.com/user-attachments/assets/a7516139-da80-4164-a2f9-5586e3b99bc3" width="200"/>

- ll /tmp/

<img src="https://github.com/user-attachments/assets/ffa37321-9364-4e03-8a28-82bed91c9f27" width="250"/>

***Confirmed presence of `host_facts.sh_DoNotDelete`.***

---

### 🔹 4. Executed Script on Each Server

- sudo ./host_facts.sh_DoNotDelete

<img src="https://github.com/user-attachments/assets/05a5e29a-966e-41e8-bcf7-32519278b6d1" width="250"/>

## Script generated inventory output under `/tmp`.

---

# 🟦 Verify Inventory Output

### 🔹 5. Checked Generated Files

- ll /tmp/

<img src="https://github.com/user-attachments/assets/a0c8e4a9-dc98-4a9e-883f-0a5c554d9b95" width="250"/>

## Confirmed:
- A new `.txt` inventory file was created  
- Contains system facts for each server  
- Ready for ingestion into the system inventory database

---

## Result
Successfully updated the system inventory database for both development servers.  
Git repository cloned, script executed, and inventory files generated under `/tmp` on **dev-app** and **dev-performance**.

## This ticket demonstrates:
- Git usage  
- Script execution  
- Inventory data collection  
- Multi‑server workflow  
