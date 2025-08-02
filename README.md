# 💸 Expense Application Deployment with Ansible

This project explains **how to deploy a 3-tier Expense Tracking Application** using **Ansible** across three different EC2 instances:

- 🗃️ MySQL Database Server
- ⚙️ Node.js Backend Server
- 🌍 Nginx Frontend Server

---

## 📦 Tech Stack

- OS: Ubuntu
- Ansible (installed on Control Node)
- MySQL
- Node.js + Express
- Nginx (with reverse proxy)

---

## 📁 Project Structure

```bash
├── ansible/
│   ├── inventory.ini
│   ├── db.yaml
│   ├── backend.yaml
│   ├── frontend.yaml
│   └── backend.service
|   ├──expense.conf
|
└── README.md
## ✅ Prerequisites Checklist

Before running the playbooks, ensure the following:

- [ ] Your `inventory.ini` file contains the correct IP addresses of the target EC2 instances.
- [ ] SSH access to each instance is set up correctly  
  (e.g., SSH key is available or has been copied using `ssh-copy-id`).
- [ ] All necessary files are present and in the correct paths:  
  - `.service` file for backend environment variables  
  - `expense.conf` for Nginx configuration
- [ ] Ansible is installed and configured properly on your control node.
- [ ] Internet access is available on the managed nodes for downloading packages and artifacts.

> 💡 Run `ansible --version` to confirm Ansible is installed.


## ▶️ Running the Playbooks

Run the following Ansible playbooks **in order**, from your Ansible control node:

```bash
ansible-playbook -i inventory.ini db.yaml
ansible-playbook -i inventory.ini backend.yaml
ansible-playbook -i inventory.ini frontend.yaml
