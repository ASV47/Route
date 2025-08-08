# 📦 LAMP Stack Setup with Ansible (Localhost)

This Ansible playbook installs and configures a **LAMP stack** (Apache2, MySQL, PHP) on a **local Ubuntu-based machine**, including UFW firewall configuration and secure MySQL setup.

## 🚀 What It Does

- Installs Apache2, PHP, and MySQL
- Configures UFW firewall (allows ports 22, 80, 443)
- Removes Apache default virtual host
- Creates MySQL user and database
- Applies secure MySQL settings
- Enables PHP for Apache2

## 🧾 Requirements

- OS: Ubuntu (or compatible)
- Ansible installed locally
- Sudo privileges

## 📂 Playbook Structure

| Feature              | Configuration                     |
|----------------------|------------------------------------|
| Apache               | Installed & configured             |
| PHP                  | Installed (with Apache module)     |
| MySQL                | Root password set, user/db created |
| UFW                  | Enabled with custom rules          |
| Hosts                | `localhost`                        |

## 🔧 How to Use

1. **Install Ansible (if not already):**
   ```bash
   sudo apt update && sudo apt install ansible -y
   ```

2. **Run the Playbook:**
   ```bash
   ansible-playbook LAMP_playbook_local.yaml
   ```

3. **Ensure UFW and Apache are active:**
   ```bash
   sudo ufw status
   sudo systemctl status apache2
   ```

## 🔐 Security Notes

- Default MySQL root password is set in the playbook:
  ```
  mysql_root_password: 01206694832awzSd
  ```
  ⚠️ **Change it before using in production.**

- MySQL User: `yasser11`  
  Database: `webdb`  
  Host: `localhost`
