# 🔧 Local Automation with Ansible — LAMP, Backup & System Setup

This repository contains a set of **Ansible playbooks** and a **Bash script** for configuring a local Ubuntu system. It includes:

- ✅ Full LAMP stack setup
- 🔐 Firewall & MySQL hardening
- 💾 Automated backup script
- 🧩 Additional modular tasks (task1–task5)

---

## 📁 File Structure

| File                    | Purpose                                 |
|-------------------------|-----------------------------------------|
| `inventory.ini`         | Ansible inventory (localhost)           |
| `LAMP_playbook_local.yaml` | Sets up Apache, MySQL, PHP, and UFW   |
| `task-backup`           | Bash script for automated backups       |
| `task1.yaml` → `task5.yaml` | Modular Ansible tasks for system ops |

---

## 🚀 Quick Start

### 1. 🔌 Prerequisites

- Ubuntu system
- Ansible installed:
  ```bash
  sudo apt update && sudo apt install ansible -y
  ```

---

### 2. 🧾 Inventory Configuration

The playbooks target `localhost`:

```ini
# inventory.ini
[local]
localhost ansible_connection=local
```

---

### 3. 📦 Run LAMP Setup

```bash
ansible-playbook -i inventory.ini LAMP_playbook_local.yaml
```

**Includes:**
- Apache, MySQL, PHP installation
- MySQL secure setup
- User `yasser11` and DB `webdb`
- UFW with ports 22, 80, 443 allowed

⚠️ MySQL Root Password: `01206694832awzSd` — Change it before production use!

---

### 4. 💾 Setup Backup Script

The `task-backup` script automates daily backups of `/var/www`.

#### Usage:

```bash
sudo cp task-backup /usr/local/bin/backup_script.sh
sudo chmod +x /usr/local/bin/backup_script.sh
```

Run it manually:

```bash
backup_script.sh
```

Or schedule it daily using cron:

```bash
crontab -e
# Add:
0 2 * * * /usr/local/bin/backup_script.sh
```

---

### 5. 🧩 Additional Tasks

Each `taskX.yaml` file (from `task1` to `task5`) contains modular automation tasks. Run them like so:

```bash
ansible-playbook -i inventory.ini task1.yaml
```

> These tasks may include copying files, managing services, creating users, and more. Review each file before execution.

---

## 🔐 Security Notes

- MySQL password is hardcoded in the LAMP playbook — replace it before use.
- Ensure `mailutils` is installed for backup alerts:
  ```bash
  sudo apt install mailutils
  ```

---

## 📬 Contact

Created by: **ahmed**  
Email used for alerts: `ahmedmohammedmahermakled@gmail.com`
