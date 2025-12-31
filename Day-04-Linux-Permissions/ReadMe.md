# Day 4: Linux File Permissions (The chmod Command)

## Objective
Grant executable permissions to a backup script `/tmp/xfusioncorp.sh` on `App Server 2` so all users can run it.

## The Solution
Used the numeric `chmod` method to set precise permissions.

**Command:**
sudo chmod 755 /tmp/xfusioncorp.sh

Verification
Checked the file status using ls -l:
Result: -rwxr-xr-x
Meaning: The owner (root) has full control, while all other users can read and execute the script.