Day 1: Secure User Creation (xFusionCorp Task)
Objective
Created a service user named javed for a backup agent tool on a remote App Server.

Technical Implementation
Remote Access: Accessed stapp01 via SSH.

Security Constraint: The user must be non-interactive to prevent unauthorized shell access.

Command used: > ``` sudo useradd -s /sbin/nologin javed
## Why /sbin/nologin?
By setting the shell to `/sbin/nologin` instead of `/bin/bash`, we ensure that even if the account credentials are compromised, an attacker cannot gain an interactive command prompt. This follows the **Principle of Least Privilege (PoLP)**.