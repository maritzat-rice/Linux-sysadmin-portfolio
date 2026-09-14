## Add Development Servers to Ansible Inventory

## Objective
Add development servers to the Ansible inventory on **dev-ansible-mr1.XX.prod1**, configure local DNS resolution, create a custom Ansible group, and validate connectivity using the Ansible ping module. This task demonstrates foundational automation and orchestration skills.

## Summary
Logged into the Ansible control node, updated `/etc/hosts`, created a custom inventory group, added dev servers, resolved SSH key issues by creating a custom Ansible configuration file, and successfully validated connectivity using `ansible -m ping`.

---

## Completed Tasks

### 🔹 1. Connected to Ansible Control Node
From Windows terminal:

ssh mrice@10.X.XX.41 
hostname

