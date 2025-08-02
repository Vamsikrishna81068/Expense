

---

## ✅ Prerequisites Checklist

Before running the playbooks, ensure the following:

- [ ] Your `inventory.ini` contains correct **private IP addresses** of all EC2 instances.
- [ ] **SSH access** is working for each instance from your control node.
- [ ] Files required for configuration are placed correctly:
  - `backend.service` — for systemd backend service
  - `expense.conf` — for Nginx reverse proxy
- [ ] **Ansible** is installed on the control node.
  > Run: `ansible --version`
- [ ] EC2 instances have **internet access** to install packages and download files.
- [ ] You have cloned or downloaded this repository to your Ansible control node.

---

## ▶️ How to Run the Playbooks

Run the following playbooks **in order** from your control node:

```bash
# 1. Setup MySQL DB
ansible-playbook -i inventory.ini db.yaml

# 2. Setup Backend (Node.js + Express)
ansible-playbook -i inventory.ini backend.yaml

# 3. Setup Frontend (Nginx + React)
ansible-playbook -i inventory.ini frontend.yaml
