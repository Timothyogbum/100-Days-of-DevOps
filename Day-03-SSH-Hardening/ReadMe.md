# Day 3: SSH Hardening - Disabling Root Login

## Objective
Restrict direct root SSH access across all application servers (`stapp01`, `stapp02`, `stapp03`) to comply with xFusionCorp security protocols.

## The Challenge (Error Report)
On the first attempt, the task failed. 
**Error:** `root login is not disabled on App Server 1`.
**Root Cause Analysis (RCA):** 1. **Configuration Drift:** The `sshd_config` file had existing commented-out lines (`#PermitRootLogin yes`) or different default values that the initial `sed` command missed.
2. **Permission Denied:** Attempting to `grep` or edit the file without `sudo` resulted in access errors.
3. **Duplicates:** Manual editing led to duplicate `PermitRootLogin` entries, causing configuration conflicts.

## The Solution (The "Clean Slate" Method)
To ensure a perfect configuration, I used a more robust automation string:
1. **Clear Clutter:** Deleted all existing instances of `PermitRootLogin`.
2. **Standardize:** Appended a single, clean `PermitRootLogin no` entry.
3. **Verify:** Used `sshd -t` to check syntax and `grep` to confirm the single entry.


# The "Sledgehammer" Command
sudo sed -i '/PermitRootLogin/d' /etc/ssh/sshd_config && \
echo "PermitRootLogin no" | sudo tee -a /etc/ssh/sshd_config && \
sudo systemctl restart sshd

Verification
sudo grep "PermitRootLogin" /etc/ssh/sshd_config -> Output: PermitRootLogin no (Single entry)
ssh root@stapp01 -> Result: Permission denied.