## Push Updated host_facts Script to GitLab

## Objective
Create a personalized version of the host_facts script, modify it to include timestamp output, and push the updated script to the GitLab repository. This task demonstrates Git proficiency, version control workflow, and Linux scripting fundamentals.

## Summary
Located the original script inside the cloned GitLab repository, created a personalized copy, added a timestamp output line, verified changes, staged and committed the file, and successfully pushed the updated script to GitLab.

---

## Completed Tasks

### 🔹 1. Connected to dev-app Server

- ssh mrice@10.X.XX.172 
- hostname 
- whoami

- Confirmed correct VM: **dev-app-mr1.XX.prod1**

---

# 🟦 Locate Script in GitLab Repository

### 🔹 2. Searched for Script Location

-	sudo find / -name "host_fact.sh_DoNotDelete" 2>/dev/null

<img src="https://github.com/user-attachments/assets/47f8eb7c-090b-4217-a974-3efc1f61947b" width="250"/>

## Output:
- /home/mrice/scripts/host_fact.sh_DoNotDelete


***Confirmed script lives inside the cloned GitLab repo.***

---

# 🟦 Create Personalized Script

### 🔹 3. Navigated to Repository

- cd ~/scripts 
- pwd

<img src="https://github.com/user-attachments/assets/0603736b-6073-41d3-aae0-98ce0f169464" width="200"/>

### 🔹 4. Copied Script

- cp host_fact.sh_DoNotDelete mrice_host_facts.sh 
- ls -l mrice_host_facts.sh

<p>
<img src="https://github.com/user-attachments/assets/d646f9b3-add1-4da4-8f1c-2efc398bfe4a" width="275"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/06869764-3314-4625-808f-66896def5c41" width="250"/>
<p>

## File successfully created.

---

# 🟦 Modify Script

### 🔹 5. Edited Script

- vi mrice_host_facts.sh

## Added at bottom of file:

- date >> "/tmp/$HOSTNAME.txt"

<img src="https://github.com/user-attachments/assets/a9ae2e54-c3a0-4ef6-b6a4-2f3d07c99e44" width="250"/>

## Saved:

- :wq

## Verified:

- cat mrice_host_facts.sh

<p>
<img src="https://github.com/user-attachments/assets/52bf6d81-4185-4ebf-9b6c-0c17dcdabd0a" width="200"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/bc934f4c-15c4-448f-b22d-899449eced6f" width="200"/>
<p>

---

# 🟦 Git Version Control Workflow

### 🔹 6. Checked Git Status

- git status

<img src="https://github.com/user-attachments/assets/cb7c2637-b2f6-4212-a1ac-de512e625aa2" width="250"/>

### 🔹 7. Staged File

- git add mrice_host_facts.sh

<img src="https://github.com/user-attachments/assets/874c1103-0511-4377-a4fb-890d39208992" width="300"/>

### 🔹 8. Committed Changes

- git commit -m "Add mrice_host_facts.sh with date output"

<p>
<img src="https://github.com/user-attachments/assets/c5acaa15-bb76-4759-a939-0ba3591e7b3e" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/adce783b-d573-4437-8ed3-75f03f74d588" width="250"/>
<p>

### 🔹 9. Pushed to GitLab

- git push

<img src="https://github.com/user-attachments/assets/7990179d-6f56-415c-ba14-bed02483a1d4" width="225"/>

## Output confirmed:
- Commit accepted  
- Remote branch updated  

<p>
<img src="https://github.com/user-attachments/assets/07dcce77-93ec-4635-afea-4f8d01480957" width="325"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/4edd639d-9af0-4298-9dbd-28803b40d881" width="325"/>
<p>

- Changes successfully uploaded  

---

## Result
Successfully created and pushed a personalized version of the host_facts script to GitLab.  
Script now includes timestamp output and is stored in version control for development team use.

## This ticket demonstrates:
- Git repository navigation  
- Script modification  
- Staging, committing, and pushing  
- Clean version‑control workflow  
