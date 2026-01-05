Day 9: Critical Incident Response - Database Recovery

Problem Statement
The Nautilus application lost connectivity to the backend database. Initial triage confirmed the mariadb service on stdb01 was down, resulting in a total application outage.

🕵️ Diagnostic Process
State Check: Used systemctl status mariadb to find the service was inactive (dead).
Failure Analysis: Attempted to start the service, which triggered a Result: exit-code.
Log Digging: Found the "smoking gun" in the logs: mariadb-prepare-db-dir failed because /var/lib/mysql was missing.

Config Audit: Verified /etc/my.cnf.d/mariadb-server.cnf to confirm that /var/lib/mysql was indeed the intended datadir.

🛠️ Resolution
Directory Reconstruction: Manually recreated the missing /var/lib/mysql directory.
Ownership Alignment: Applied chown -R mysql:mysql to the directory. This is critical because the MariaDB daemon runs as a non-privileged user and cannot initialize data in a directory it doesn't own.

Service Restoration: Successfully executed systemctl start mariadb and systemctl enable mariadb.

💡 Why This Is Important (The "Smart" Take)
Service Dependencies: Services like MariaDB have ExecStartPre conditions in their unit files. If the environment (folders, permissions, configs) isn't perfect, the service won't even try to start.

Data Integrity: In DevOps, we don't just "force start" things. We look at why they failed to ensure we aren't masking a deeper issue like disk failure or permission drift.

Persistence: By using enable, we moved from a reactive fix (starting it now) to a proactive configuration (ensuring it survives a reboot).