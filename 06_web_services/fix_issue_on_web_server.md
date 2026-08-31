## Fix Issue on Web Server (CheckMK Monitoring Alert)

## Objective
Investigate and resolve a monitoring alert for **stage-web-mr1.XX.prod1** reported by CheckMK.  
This task demonstrates practical monitoring, service validation, and alert remediation skills.

## Summary
CheckMK reported an NTP synchronization issue on **stage-web**.  
After logging into the server, verified that `chronyd` was running normally.  
The alert was caused by stale monitoring data, not an actual service failure.  
Performed a CheckMK rescan and activated changes, clearing the alert successfully.

---

## Completed Tasks

### 🔹 1. Reviewed Alert in CheckMK

**Navigated:**

- Setup → Hosts → Main → Dev → stage-web-mr1.XX.prod1

<img src="https://github.com/user-attachments/assets/b37d2cdf-bf0c-4f98-91f4-5a2f5cc5496e" width="300"/>

**Observed:**
- **NTP Time** check was critical  
- Server had “not synchronized in over 8 hours”  
- Likely stale data or unreachable NTP source

<img src="https://github.com/user-attachments/assets/5727d70b-af3a-44a9-9283-10c8ac38c0a7" width="300"/>

---

## Server Validation

### 🔹 2. Logged Into Stage-Web

**From bastion:**

- ssh mrice@10.X.XX.176 
- hostname 
- whoami 
- sudo -i 

<img src="https://github.com/user-attachments/assets/2aa7b74f-53b4-4496-acba-4af88d250e63" width="150"/>

### 🔹 3. Checked NTP Service

- systemctl status chronyd

<img src="https://github.com/user-attachments/assets/a39abe4f-1294-4612-a685-f2f44f55129c" width="250"/>

**Result:**
- `chronyd` was **running normally**
- No errors, no failures, no drift issues

This confirmed the alert was **not caused by a real service failure**.

---

## CheckMK Remediation

### 🔹 4. Forced CheckMK to Refresh Service Data

**In CheckMK:**
- Selected **Rescan** on the host  
- Forced CheckMK to pull fresh NTP data  
- Alert cleared immediately

<p>
<img src="https://github.com/user-attachments/assets/7352cee5-f75a-419e-b938-5734432fd8fd" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/09222489-e240-416b-864e-ff7321862e26" width="300"/>
<p>

### 🔹 5. Activated Changes

**Clicked:**

- 1 change → Activate

<p>
<img src="https://github.com/user-attachments/assets/ff973b1f-6875-4382-bdd1-a64388544b2f" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/4107ad0f-9727-471e-ba4f-e233e9217b12" width="300"/>
<p>

<p>
<img src="https://github.com/user-attachments/assets/2b50a9f7-3faf-4771-a651-b5f2c3d63dff" width="300"/>
<p>

*Monitoring state updated successfully.*

---

## Result
The NTP alert on **stage-web-mr1.XX.prod1** was resolved.  
`chronyd` was healthy, and the issue stemmed from stale monitoring data.  
A CheckMK rescan and activation of changes restored the host to an **OK** state.

This ticket demonstrates real monitoring workflow:
- Alert review  
- Root‑cause validation  
- Service inspection  
- Monitoring refresh  
- Change activation  
