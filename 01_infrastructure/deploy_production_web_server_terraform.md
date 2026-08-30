# Deploy Production Web Server from Template

## Objective
Provision a production web server using Terraform and deploy it into the correct vSphere resource pool. This task demonstrates infrastructure automation, template customization, and successful VM provisioning through Infrastructure as Code (IaC) platforms (Terraform).

---

## Task Summary
Use Terraform to deploy a newly fixed web server into production. The VM must be created inside the appropriate vSphere resource pool and powered on successfully.

---

## Requirements
- VM Name: **prod-webserver**
- Deployment Method: **Terraform**
- Successful provisioning and placement in the correct resource pool
- VM must power on without errors

---

## Steps Performed

### 1. Access Deployment Host

**SSH’d into the automation host from the bastion.**

**Verified environment:**
- hostname 
- whoami

<img src="https://github.com/user-attachments/assets/a04d983d-a641-4693-a29a-c76e32ba52e3" width="200"/>

---

### 2. Check for Existing Terraform Project Directory

- ls ~

<img src="https://github.com/user-attachments/assets/4f4c4645-6c9d-4484-a6ad-ccf55a77c770" width="250"/>

*No Terraform directory existed.*

---

### 3. Clone Terraform Project

- cd ~ git clone git@gitlab.com:<redacted>/terraform.git

<img src="https://github.com/user-attachments/assets/274391f7-1645-49bd-920e-d70758acfaef" width="250"/>

---

### 4. Enter Project Directory

- cd terraform ls

<img src="https://github.com/user-attachments/assets/982ea046-ad49-4072-97f3-603e5e4bc157" width="250"/>


**Project files confirmed:**
- main.tf  
- variables.tf  
- terraform.tfvars  
- output.tf  
- scripts/

---

### 5. Update terraform.tfvars

**Opened the variables file:**
- vi terraform.tfvars

<img src="https://github.com/user-attachments/assets/d74e3366-e6c3-4944-aa46-ed3243d7f097" width="250"/>

**Updated fields:**

- `vsphere_datastore` → `"DS-01"`
- `vsphere_network` → `"YT-Intran-VLAN"`
- `vsphere_resource_pool` → `"MRICE-CLUSTER"`
- `vsphere_virtual_machine_template` → updated to correct template
- `vsphere_virtual_machine_name` → `"prod-webserver-mr1"`

<img src="https://github.com/user-attachments/assets/bcaf4b48-20c4-4b49-b963-2b8cb8c59566" width="250"/>

*All sensitive names and identifiers have been redacted.*

---

### 6. Initialize Terraform

**terraform init**

<p>
<img src="https://github.com/user-attachments/assets/01c14d5b-af70-4f95-842b-6d2d7a003d70" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/f2f7f69a-cbf6-4427-883d-4d5f91f7096c" width="250"/>
<p>
  
*Terraform downloaded the vSphere provider and initialized the working directory.*

---

### 7. Review Planned Changes

**terraform plan**

Terraform successfully read:

- Datacenter  
- Resource pool  
- Template UUID  
- Network  
- Datastore  

Plan showed **1 resource to be created**.

<p>
<img src="https://github.com/user-attachments/assets/a24fce89-a3ff-440f-85a3-52d1783775e2" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/9da0fdb6-f80f-4088-8170-5057fbcee0e7" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/8b125df7-9185-4420-99d7-f486fb03c390" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/133c38c9-8190-41bf-bb5f-d5b0c3ed735f" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/7c69966d-6b57-4967-aa5a-2645a8709659" width="250"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/796ca87d-6fb3-4251-8dea-10eeb62c95e7" width="250"/>
<p>


---

### 8. Apply Deployment

**terraform apply**

<img src="https://github.com/user-attachments/assets/50e30f57-21aa-49b9-bbe2-ce40eabf0ab7" width="250"/>

Approved the changes when prompted.

**Terraform:**
- Cloned the correct vSphere template  
- Applied guest customization  
- Set hostname: **prod-webserver-mr1**  
- Placed the VM in the correct resource pool  
- Attached the correct network  
- Powered on the VM  
- Completed provisioning in **3m48s**  

**Final result:**

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

<img src="https://github.com/user-attachments/assets/c730ecdc-196e-4398-8bb0-b38ea7bf69b8" width="250"/>

---

## Verification

- VM appears in vSphere under the correct resource pool  

<img src="https://github.com/user-attachments/assets/7b1290c8-5306-4240-80e9-0023b055aa5f" width="250"/>

- VM is powered on  
- Datastore and network assignments match expected configuration  
- Guest customization applied successfully  
- Template clone and provisioning completed without errors  

---

## Deployment Summary
Successfully deployed the production web server using Terraform automation.

- Updated `terraform.tfvars` with correct datastore, network, resource pool, and template values  
- Ran `terraform init`, `terraform plan`, and `terraform apply` without issues  
- Template cloned and customization applied correctly  
- VM created as **prod-webserver-mr1** in the correct resource pool  
- VM powered on successfully  
- Deployment validated in vSphere  

**Deployment completed successfully.**

