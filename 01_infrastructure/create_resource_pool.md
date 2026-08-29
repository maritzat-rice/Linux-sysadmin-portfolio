## Create Resource Pool in vSphere

## Objective
Organize and allocate compute resources efficiently by creating a dedicated resource pool for virtual machines. This task demonstrates foundational virtualization administration skills including resource pool creation, VM migration, and inventory management.

## Summary
Created a new vSphere resource pool named **MRICE-CLUSTER** and migrated the VM **dev-app-XX1.XX.prod1** into it. Verified that the VM now inherits compute resources from the newly created pool. This improves organization, resource allocation, and future scalability.

---

## Completed Tasks

### 🔹 1. Created a New Resource Pool
Steps:
1. Logged into vSphere.
2. Right‑clicked the **Data Center** object.
3. Selected **New Resource Pool**.


<img src="https://github.com/user-attachments/assets/f79928d7-d477-46ed-96b8-1ef0d694507d" width="250"/>

4.	Named the pool: **MRICE-CLUSTER**.

<img src="https://github.com/user-attachments/assets/b34afb29-9b92-4da0-aadf-db8fc6884016" width="250"/>

5. Left CPU and Memory shares/limits at default values (per internal wiki guidance).
6. Clicked **OK**.

**Verification:**  
Resource pool **MRICE-CLUSTER** appeared in the left‑side navigation pane.

<img src="https://github.com/user-attachments/assets/16938e45-eac5-464f-a742-b04d7abc06ba" width="250"/>

---

### 🔹 2. Migrated VM into Resource Pool
VM: **dev-app-XX1.XX.prod1**

Steps:
1.	Right‑clicked the VM → **Migrate**.

<img src="https://github.com/user-attachments/assets/adfa516e-55d7-4661-94f1-7e613a2fee83" width="250"/>

2.	Selected **Change compute resource only** → Next.

<img src="https://github.com/user-attachments/assets/7de692dd-4a84-47a0-9752-2f9e3ca51774" width="250"/>

3. Under Resource Pools, selected **MRICE-CLUSTER**.
4. No changes required on:
   - Select Networks  
   - vMotion Priority  
5. Confirmed selection → **Finish**.

<img src="https://github.com/user-attachments/assets/22657fef-feea-497a-b153-dbba9e5ae8ca" width="250"/>

---

### 🔹 3. Verified Resource Pool Assignment
On the VM’s **Summary** tab:
- Under **Resource Pool**, the VM now shows **MRICE-CLUSTER**.
- Confirmed the VM appears under the resource pool in the inventory tree.

<img src="https://github.com/user-attachments/assets/0a170cd9-b0bb-4c44-afcc-ac5ceac4e8c1" width="250"/>

---

## Result
The resource pool **MRICE-CLUSTER** was successfully created and the VM **dev-app-XX1.XX.prod1** was migrated into it. This improves compute resource organization and prepares the environment for future VM deployments.

---

## 🔹 Sub Task: Migration Workflow Review (VM → Resource Pool)

### Objective
Revisit and validate the VM migration workflow to ensure proper placement within the newly created resource pool and reinforce confidence in compute resource mobility.

### Title
Migration Workflow Review for VM dev-app-mr1.XX.prod1

### Summary
After creating the resource pool, the VM migration workflow was reviewed to confirm correct placement and validate that the VM was already assigned to the intended compute resource. This exercise reinforces familiarity with vSphere’s migration options and resource pool hierarchy.

### Steps Reviewed
- Navigated to **Hosts and Clusters**.
- Right clicked the VM → **Migrate**.

<img src="https://github.com/user-attachments/assets/07965435-3c76-4444-9429-bef43d7f0cd2" width="250"/>

- Selected **Change compute resource only**.

<img src="https://github.com/user-attachments/assets/64d12a28-68c9-4894-8d1e-2eff24aac5d5" width="250"/>

- Switched the wizard view to **Resource Pools**.

<img src="https://github.com/user-attachments/assets/8def5e9a-3ab4-4864-b982-eaaed70402e5" width="250"/>

- Verified that the VM was already assigned to **MRICE-CLUSTER**.

### Verification
- VM Summary tab shows Resource Pool: **MRICE-CLUSTER**.

<img src="https://github.com/user-attachments/assets/b06e24db-2efb-4351-bade-a8702b04bd35" width="250"/>

- VM appears under the resource pool in the left hand inventory tree.

### Result
No migration was required.  
This review served as a validation exercise to reinforce confidence in VM mobility, compute resource assignment, and correct resource pool placement.



