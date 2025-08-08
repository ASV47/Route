# 🛠️ `backup_script.sh` — Daily Backup Automation

This is a Bash script that automates daily backups of a source directory. It supports:

- Automatic backup to a destination directory
- Logging with rotation
- Error email notifications
- Retention policy for old backups

## 📁 Directory Structure

| Variable              | Description                      | Default Value                  |
|-----------------------|----------------------------------|--------------------------------|
| `SOURCE_DIR`          | Directory to back up             | `/var/www`                     |
| `BACKUP_DIR`          | Backup destination               | `/backups`                     |
| `LOG_FILE`            | Log file path                    | `/var/log/backup_script.log`   |
| `RETENTION_DAYS`      | Days to keep backups             | `7`                            |
| `LOG_RETENTION_COUNT` | Number of rotated logs kept      | `5`                            |
| `RECIPIENT_EMAIL`     | Email for failure notifications  | your email                     |

## 🧪 How to Use

1. **Place the script:**
   ```bash
   sudo cp task-backup /usr/local/bin/backup_script.sh
   sudo chmod +x /usr/local/bin/backup_script.sh
   ```

2. **(Optional) Edit variables inside the script** to match your environment.

3. **Run manually:**
   ```bash
   /usr/local/bin/backup_script.sh
   ```

4. **Schedule with cron for daily runs:**
   ```bash
   crontab -e
   # Add this line:
   0 2 * * * /usr/local/bin/backup_script.sh
   ```

## 📨 Notifications

If the backup fails, the script will send an alert email to the configured recipient using `mail`. Make sure:

- `mailutils` or `mailx` is installed
- The system is configured to send mail (e.g. via postfix)

## 🧹 Cleanup & Rotation

- Backups older than `RETENTION_DAYS` are deleted.
- Logs are rotated up to `LOG_RETENTION_COUNT` times.
