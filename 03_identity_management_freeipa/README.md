# Identity Management (FreeIPA)

This folder contains hands-on identity management tasks completed using **FreeIPA**, a centralized authentication and account management solution commonly used in Linux environments. These tasks demonstrate practical experience with user provisioning, group management, client configuration, and directory queries — core skills for Linux System Administration and foundational Identity & Access Management (IAM).

---

## 📌 Overview

FreeIPA provides:
- Centralized user and group management  
- Kerberos-based authentication  
- LDAP directory services  
- Host-based access control  
- Certificate management  

These tasks simulate real-world administrative work performed in enterprise Linux environments.

---

## 📁 Task Breakdown

### **Install & Configure FreeIPA Client**
This task covers enrolling a Linux VM into FreeIPA:
- Installing FreeIPA client packages  
- Running `ipa-client-install`  
- Configuring SSSD and Kerberos  
- Validating enrollment  
- Troubleshooting DNS and connectivity issues  

This represents foundational IAM integration work for Linux hosts.

---

### **Create User in FreeIPA**
This task demonstrates user provisioning through the FreeIPA Web UI:
- Creating a new user account  
- Setting initial attributes  
- Assigning default group memberships  
- Verifying account creation  
- Documenting the workflow with screenshots  

This mirrors real onboarding tasks performed by SysAdmins.

---

### **Add User to Group**  
*(Included as a subsection inside the “Create User” task)*

This sub-task extends the user creation workflow by modifying group membership:
- Navigating the User Groups tab  
- Adding the user to the appropriate group  
- Verifying direct membership updates  

This reflects incremental IAM changes requested by HR or team leads.

---

### **Configure FreeIPA Client on Stage VM**
This task focuses on troubleshooting and configuring FreeIPA enrollment on a staging VM:
- Diagnosing DNS discovery failures  
- Validating LDAP connectivity  
- Reviewing logs for enrollment errors  
- Attempting client installation  
- Documenting root cause and next steps  

This showcases deeper troubleshooting skills and understanding of FreeIPA’s backend components.

---

### **Get List of All FreeIPA Users**
This task demonstrates directory querying and reporting:
- Using `ipa user-find`  
- Redirecting output to a file  
- Reviewing user attributes  
- Delivering a clean user list for HR or auditing  

This aligns with IAM reporting and compliance tasks.

---

## 🧩 Skills Demonstrated

- Identity & Access Management (IAM)  
- FreeIPA administration  
- User provisioning  
- Group membership management  
- Host enrollment & client configuration  
- SSSD & Kerberos troubleshooting  
- LDAP queries and reporting  
- Documentation of administrative tasks  
- Root cause analysis  








