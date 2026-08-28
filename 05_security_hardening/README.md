### 🔐 Security Hardening
This section of my Linux SysAdmin portfolio demonstrates practical, real world security hardening tasks performed on enterprise Linux systems. Each ticket represents a focused security improvement, including firewall configuration, service restrictions, vulnerability scanning, remediation, and system auditing.

The work in this folder reflects hands on experience with:
- Firewalld (port management, service rules, non standard ports)
- Apache HTTPD (secure access, maintenance workflows)
- SSH hardening (root login restrictions, bastion host enforcement)
-	Ansible automation (closing ports, enforcing security policies)
-	Lynis auditing (system level security assessments)
-	OpenVAS vulnerability scanning (initial scan + remediation validation)

Each ticket includes:
-	A clear objective
-	Completed tasks
-	Verification steps
-	Screenshots or PDF artifacts
-	Final results

### 📁 Ticket Index
### SSH Hardening
-	disable-ssh-root-login.md — Disabled root login to reduce attack surface
-	restrict-ssh-to-bastion.md — Enforced SSH access only through a bastion host

### Firewall & Apache Hardening
-	block-malicious-ip.md — Blocked malicious IP traffic
-	allow_http_nonstandard_port.md — Allowed HTTP on a non standard port
-	apply_apache_firewall.md — Allowed Apache through firewalld
-	close_ports_via_ansible_playbook.md — Closed unused ports using Ansible automation

### Maintenance Workflow
-	notify_website_under_maintenance.md — Enabled maintenance banner
-	remove_maintenance_banner.md — Removed maintenance banner after service restoration

### System Auditing
-	security_audit_lynis.md — Performed a full Lynis security audit

### Vulnerability Scanning & Remediation
-	openvas_vulnerability_scan/ — Initial OpenVAS scan + PDF report
-	fix_vulnerabilities/ — Remediation steps + validation rescan PDF

### 🧩 Project Summary
This Security Hardening project simulates the responsibilities of a Linux SysAdmin working in a production environment. The tickets demonstrate:
-	Identifying vulnerabilities
-	Applying secure configurations
-	Automating fixes
-	Validating remediation
-	Documenting results clearly
Together, these tasks show end to end security lifecycle management — from detection to remediation to verification.

### 📄 Artifacts
Each folder contains Markdown documentation and supporting evidence such as:
-	OpenVAS scan reports (PDF)
-	Lynis audit results
-	Command outputs
-	Screenshots
-	Verification steps
These artifacts provide proof of work and demonstrate real world troubleshooting and security implementation.

### 🎯 Skills Demonstrated
-	Linux system hardening
-	Firewall configuration
-	Apache security
-	SSH access control
-	Vulnerability scanning
-	Remediation workflows
-	Ansible automation
-	Security auditing
-	Professional documentation

