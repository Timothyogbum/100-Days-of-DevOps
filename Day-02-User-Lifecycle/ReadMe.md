# Day 2: Temporary Access & Account Expiry

## Objective
Create a temporary user `john` on `App Server 3` with a hard expiration date of **2024-03-28**.

## Technical Implementation
1. **Remote Access:** Connected to `stapp03` via SSH as `banner`.
2. **Command:**
   sudo useradd -e 2024-03-28 john

Verification: Used the chage (Change Age) tool to verify the expiration
sudo chage -l john