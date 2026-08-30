# Infrastructure (vSphere, VM Deployment, Resource Pools, Snapshots, Kickstart, Veeam, Terraform)

This folder contains foundational infrastructure tasks performed in a vSphere environment. These tasks demonstrate core virtualization skills, VM lifecycle management, automation, backup configuration, and template based provisioning. Each item reflects real-world SysAdmin responsibilities and showcases hands-on experience with enterprise infrastructure tools.

---

## 📌 Overview

The tasks in this folder cover:

- Deploying virtual machines on vSphere  
- Creating and managing resource pools  
- Migrating VMs between compute resources  
- Using Kickstart for automated OS installation  
- Creating VM snapshots for safe rollback  
- Installing and configuring Veeam backup agents  
- Deploying production servers using Terraform automation  

These workflows represent essential infrastructure operations performed in modern datacenter environments.

---

## 📁 Task Breakdown

### **Deploy CentOS Stream 9 VM on vSphere**
Provisioned a new CentOS Stream 9 virtual machine using vSphere’s VM creation workflow.  
Configured CPU, memory, storage, network, and mounted ISO media.  
Validated successful OS installation and VM readiness.

---

### **Create Resource Pool**
Created a dedicated resource pool within the vSphere cluster to organize and manage compute resources.  
Configured pool settings and validated placement in the cluster hierarchy.

---

### **Migrate VM to Resource Pool**
Reviewed and practiced the VM migration workflow.  
Verified that the VM was correctly assigned to the intended resource pool and confirmed placement through the vSphere inventory and VM Summary tab.

---

### **Spin Up Web Server Using Kickstart**
Used a Kickstart configuration to automate the deployment of a web server.  
Performed unattended installation, applied custom configuration, and validated successful provisioning.  
Demonstrated automated OS deployment at scale.

---

### **Create Snapshot**
Created a VM snapshot to preserve system state prior to maintenance or configuration changes.  
Verified snapshot creation and documented rollback considerations.

---

### **Install & Configure Veeam Standalone Linux Agent**
Installed the Veeam backup agent on a Linux VM.  
Configured backup jobs, validated connectivity, and ensured the VM was protected by scheduled backups.  
Demonstrated backup readiness and disaster recovery fundamentals.

---

### **Deploy Production Web Server Using Terraform**
Used Terraform to automate deployment of a production web server into the correct vSphere resource pool.  
Updated variables, initialized Terraform, reviewed the plan, and applied changes.  
Validated template cloning, guest customization, resource pool placement, network assignment, and successful VM power-on.  
Showcased Infrastructure as Code (IaC) and vSphere automation.

---

## 🧩 Skills Demonstrated

- vSphere administration  
- VM provisioning and lifecycle management  
- Resource pool creation and compute organization  
- VM migration workflows  
- Automated OS deployment (Kickstart)  
- Snapshot management  
- Backup configuration (Veeam)  
- Terraform automation and Infrastructure as Code  
- Documentation and validation of infrastructure tasks  

These skills reflect real-world SysAdmin responsibilities and support my long-term transition into cybersecurity by demonstrating strong foundational infrastructure knowledge.




