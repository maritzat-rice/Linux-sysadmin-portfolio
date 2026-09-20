## Create Your Own GitLab Repository

## Objective
Create a personal GitLab repository to store Ansible playbooks and Bash scripts for documentation, version control, and collaboration. This task demonstrates GitLab project creation, repository structuring, and public visibility configuration.

## Summary
Logged into GitLab, created a new public project, initialized it with a README, added directories for Ansible and scripts, and prepared the repository for uploading automation content. Verified repository structure and committed initial files.

---

## Completed Tasks

### 1. Logged Into GitLab
- Logged in using personal GitLab account: **marixxxxxx@xxxl.com**
- Navigated to: **Projects → New Project**

<img src="https://github.com/user-attachments/assets/4b3b2351-81c3-4921-8c6a-cd292cc8e9ad" width="300"/>

### 2. Created a New Blank Project

## Selected:
- **Create Blank Project**
- **Project Name:** `ansible-and-scripts`
- **Namespace:** `maritzat.rice`
- **Visibility:** **Public**  
  ***(Allows access without authentication)***

## Enabled:
- **Initialize repository with a README**

## Clicked:
- **Create project**

<p>
<img src="https://github.com/user-attachments/assets/98f7bb89-72a9-475c-8a7e-d67f9396cd3c" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/26816a0c-3ec2-4789-8a14-a40ffddb0a8f" width="300"/>
<p>

***Repository successfully created.***


### 3. Created Required Directories

## Inside the new project:
- Clicked **+**
- Selected **New directory**
- Created:
  - `ansible/`
  - `scripts/`

<p>
<img src="https://github.com/user-attachments/assets/36876592-7094-41f0-a245-b90a8b89481e" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/27f78907-e745-4626-a93c-761e9013cdca" width="250"/>
<p>

## Committed changes to the **main** branch.

## GitLab confirmed:
- `ansible/` directory created  
- `scripts/` directory created  
- `.gitkeep` placeholder files added automatically

<img src="https://github.com/user-attachments/assets/87b08ad5-5490-4270-909c-4103e4a95b47" width="250"/>

### 4. Navigated Into Directories

## Viewed project file list showing:
- `ansible/`
- `scripts/`
- `README.md`

<img src="https://github.com/user-attachments/assets/aa05a743-6cab-40fb-8d2d-06e14e2a3bf8" width="250"/>

***Confirmed directories were created successfully and ready for uploads.***


### 5. Uploaded Ansible Playbooks

- Uploaded multiple `.yml.docx` files into the repository, including:

### **create-scripts-dir.yml.docx**

<p>
<img src="https://github.com/user-attachments/assets/5258137e-ce36-4eb6-8584-d4d9b7755ac4" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/ef729795-dc8c-44be-b4aa-569a9d782643" width="250"/>
<p>

## Commit message:

- Upload playbooks and scripts document

<img src="https://github.com/user-attachments/assets/c2765b5d-edc3-4353-9328-ca3301263f64" width="250"/>

### **dev-hostfacts.yml.docx**

<p>
<img src="https://github.com/user-attachments/assets/c0c4caa1-d092-4241-8151-766df2a61a6d" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/7975c3f1-f10d-4124-bc05-e4709503a184" width="250"/>
<p>

## Commit message:

- Ticket XX playbook: run host facts script on dev-app and dev-performance

<img src="https://github.com/user-attachments/assets/c847f9de-0ba8-42c8-b284-9eaba9e4b08f" width="225"/>

- Committed each upload to the **main** branch with descriptive commit messages.


### **close_ports.yml.docx**

<p>
<img src="https://github.com/user-attachments/assets/bb9be26c-f2c1-4b8b-9d38-cd068f3a1dc2" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/b714f1e1-0417-4aa4-96df-0d37b7975c0d" width="250"/>
<p>

## Commit message:

- Ticket XX playbook: close required ports on dev servers

<img src="https://github.com/user-attachments/assets/64ab7e27-754c-40f0-9114-0862f4fa6d54" width="250"/>

### **dev-mr-patch.yml.docx**

<p>
<img src="https://github.com/user-attachments/assets/37b7f0f3-85e6-47f4-9507-e39a35563d4e" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/4b84ac81-dd54-4b70-8afe-945289a2bbcc" width="250"/>
<p>

## Commit message:

- Add dev-mr-patch.yml playbook for patching dev servers

<img src="https://github.com/user-attachments/assets/2aa24b0b-7c46-46bf-97c5-45962fd027c3" width="250"/>

All commits were made to the **main** branch.

---

## 6. Verified Playbook Contents

## Screenshots in the PDF confirm the uploaded playbooks include:

- Directory creation playbook (`create-scripts-dir.yml`)
- Host facts automation (`dev-hostfacts.yml`)
- Firewall port closure (`close_ports.yml`)
- Dev server patching (`dev-mr-patch.yml`)

***Each file was successfully committed and visible in the GitLab file tree.***

---

## Result
Successfully created a **public GitLab repository** containing directories for Ansible playbooks and Bash scripts. Uploaded multiple automation playbooks and verified commit history and repository structure.

## This ticket demonstrates:
- GitLab project creation  
- Repository structuring  
- Public visibility configuration  
- Uploading automation playbooks  
- Commit history management  
- Documentation best practices  
