# 💸 Expense Application Deployment with Ansible

This project shows how to deploy a **3-tier Expense Tracking Application** using **Ansible** across three different EC2 instances:

- 🗃️ **MySQL Database Server**
- ⚙️ **Node.js Backend Server**
- 🌍 **Nginx Frontend Server**

---

## 📦 Tech Stack

- OS: Ubuntu 22.04 (or Amazon Linux for Ansible)
- Configuration Manager: **Ansible**
- Database: **MySQL**
- Backend: **Node.js** (Express.js)
- Frontend: **Nginx** (static React build)

---

## 📁 Project Structure

```bash
├── Expense/
│   ├── inventory.ini         # Inventory with EC2 IPs
│   ├── db.yaml               # Playbook for MySQL DB setup
│   ├── backend.yaml          # Playbook for Node.js backend
│   ├── frontend.yaml         # Playbook for Nginx frontend
│   ├── backend.service       # systemd service for backend
│   └── expense.conf          # Nginx config for frontend routing
│
└── README.md                 # Project deployment documentation




---

## ✅ Prerequisites Checklist

Before running the playbooks, ensure the following:

- Your `inventory.ini` contains correct **private IP addresses** of all EC2 instances.
- **SSH access** is working for each instance from your control node.
-  Files required for configuration are placed correctly:
  - `backend.service` — for systemd backend service
  - `expense.conf` — for Nginx reverse proxy
- **Ansible** is installed on the control node.
  > Run: `ansible --version`
-  EC2 instances have **internet access** to install packages and download files.
- You have cloned or downloaded this repository to your Ansible control node.

---

## ▶️ How to Run the Playbooks

Run the following playbooks **in order** from your control node:

```bash
# 1. Setup MySQL DB
ansible-playbook -i inventory.ini db.yaml

# 2. Setup Backend (Node.js + Express)
ansible-playbook -i inventory.ini backend.yaml

# 3. Setup Frontend (Nginx )
ansible-playbook -i inventory.ini frontend.yaml
