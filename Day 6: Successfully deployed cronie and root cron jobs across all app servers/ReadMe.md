Day 6: Cron Job Automation

Challenge: Deploy a recurring task across multiple CentOS/RHEL servers.

Solution: Installed the cronie package and used systemctl enable --now crond for immediate and persistent service availability.

Key Command: Used sudo crontab -u root - to programmatically inject cron jobs, ensuring the task was associated with the correct administrative user.

Lesson Learned: Always verify the crontab for the specific user requested in the ticket. A job in tony's crontab is not the same as a job in root's crontab!