![Ansible CI](https://github.com/amankothiyal04/Ansible-Autohealing-nginx/actions/workflows/ansible-ci.yml/badge.svg)
# 🚀 Ansible Auto-Heal NGINX Deployment

# 🚀 Ansible Auto-Heal NGINX Deployment

This project automates the **deployment, validation, and self-healing** of NGINX web servers using **Ansible**.  
It includes email notifications (via AWS SES) for both **successful deployments** and **failure rollbacks** — ensuring reliability and visibility in production environments.

---

## 🧠 Features

- ✅ Dynamic Inventory using AWS EC2 plugin  
- ✅ Automated NGINX installation and configuration  
- ✅ Configuration validation and rollback (self-healing)  
- ✅ Email notifications for success/failure  
- ✅ Encrypted credentials via Ansible Vault  
- ✅ Modular structure following Ansible best practices  

---

## 🏗️ Project Structure
ansible-autoheal-nginx/

├── ansible.cfg
├── aws_ec2.yml
├── deploy.yml
└── roles/
└── nginx/
├── defaults/
├── handlers/
├── tasks/
└── templates/

---

## 🧩 Workflow Overview

1. **Ansible Controller** connects to EC2 instances using the AWS dynamic inventory.
2. Deploys NGINX on all instances tagged `App=nginx`.
3. Validates configuration with `nginx -t`.
4. If configuration fails → **rollback** + send failure email.
5. If success → send confirmation email via **AWS SES**.

---

## ⚙️ Technologies Used
- **Ansible**
- **AWS EC2**
- **AWS SES**
- **Ubuntu**
- **YAML / Jinja2**
- **Ansible Vault**

---

## 🚨 Auto-Healing Logic
- Backup configuration before every deployment.
- If the playbook detects a failed NGINX restart:
  - Restore from backup.
  - Restart service again.
  - Send failure notification.

---

## 📬 Notifications
- Uses **AWS Simple Email Service (SES)** to send:
  - ✅ Success mail for healthy deployments.
  - ❌ Failure mail for configuration or restart errors.

---

## 🧰 Future Enhancements
- Slack / Discord integration for team alerts.
- Terraform integration to auto-provision EC2.
- Jenkins or GitHub Actions-based pipeline for CI/CD.

---
