Day 10: Automated News Site Backup (App Server 3)
Status: Completed ✅

🚩 The Mission
Automate the backup of the /var/www/html/news directory on App Server 3 and transfer it silently to the Nautilus Backup Server.

🚧 Hurdles Faced & Resolutions
Pathing Mismatch: Initially targeted the wrong directory (/official). I resolved this by performing a system-wide search (find) to locate the correct source path (/news).

Authentication Blockers: The script stalled at password prompts. I established RSA key-pair trust between the banner user and the clint backup user to enable "headless" transfers.

User Discrepancy: Navigated a mismatch where the lab credentials pointed to user clint but the initial script logic used clark. Correcting this was the key to final validation.

Strict Naming Conventions: Learned that automated validation scripts require exact matches for filenames (news_backup.sh and xfusioncorp_news.zip).

💡 Key DevOps Takeaway
Automation isn't just about the code; it's about Environment Awareness. A script is only as good as the permissions, paths, and trust relationships it relies on.