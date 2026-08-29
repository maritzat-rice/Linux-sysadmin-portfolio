## Create Snapshots for All Virtual Machines (Pre‑Maintenance)

## Objective
Prepare for a company‑wide maintenance window by creating snapshots of all assigned virtual machines. This ensures rollback capability and protects system integrity during infrastructure updates.

## Summary
Created pre‑maintenance snapshots for all assigned VMs:
- **dev-app-mr1.XX.prod1**
- **dev-performance-mr1.XX.prod1**
- **stage-web-mr1.XX.prod1**

Each snapshot was named consistently and included a clear description for audit and change‑management tracking.

---

## Completed Tasks

### 🔹 1. Snapshot: dev-app-mr1.XX.prod1
Steps:
1.	Selected VM: **dev-app-mr1.XX.prod1**

<img src="https://github.com/user-attachments/assets/24a8e82e-11dc-49c5-af43-dd46588232a3" width="250"/>

2. Clicked **Snapshots** in the vSphere ribbon
3. Selected **Take Snapshot**
4. Entered:
   - **Name:** `pre-maintenance 2026-03-10`
   - **Description:** Snapshot created before company-wide maintenance as required by ticket.
5. Clicked **Create**

<img src="https://github.com/user-attachments/assets/1368ce58-a026-4aa2-916e-b2799c34c408" width="250"/>

**Snapshot successfully created.**

---

### 🔹 2. Snapshot: dev-performance-mr1.XX.prod1
Steps:
1.	Selected VM: **dev-performance-mr1.XX.prod1**
2.	Snapshots → **Take Snapshot**

<img src="https://github.com/user-attachments/assets/44039e6b-2bcb-4695-9e61-ca000317c7c7" width="250"/>

3. Entered:
   - **Name:** `pre-maintenance 2026-03-10`
   - **Description:** Snapshot created before company-wide maintenance as required by ticket.
4. Clicked **Create**

<img src="https://github.com/user-attachments/assets/30570cd6-8c1b-4fbe-a4c7-86c8ae054f56" width="250"/>

**Snapshot successfully created.**

---

### 🔹 3. Snapshot: stage-web-mr1.XX.prod1
Steps:
1.	Selected VM: **stage-web-mr1.XX.prod1**

<img src="https://github.com/user-attachments/assets/b6fedcd5-0fc3-48eb-8ebb-e2214ed2b355" width="250"/>

2. Snapshots → **Take Snapshot**
3. Entered:
   - **Name:** `pre-maintenance 2026-03-10`
   - **Description:** Snapshot created before company-wide maintenance as required by ticket.
4. Clicked **Create**

<img src="https://github.com/user-attachments/assets/1ce00d2b-bfbd-4b96-b27b-5f7cfaa51007" width="250"/>

**Snapshot successfully created.**

<img src="https://github.com/user-attachments/assets/febd18ad-dae7-4a00-a822-91d59da74fa3" width="250"/>

---

## Result
All assigned VMs now have consistent, clearly labeled pre‑maintenance snapshots.  
This ensures safe rollback capability during the upcoming company‑wide maintenance window and demonstrates proper change‑management procedures.



