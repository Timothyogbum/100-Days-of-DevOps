The Task: Enable the thor user on the Jump Host to access all application servers (stapp01, stapp02, stapp03) without a password.

The "Why" - Why is this important?

Automation Scalability: In a modern DevOps environment, we don't manage one server; we manage hundreds. Password-less SSH allows scripts and orchestration tools (like Ansible) to execute commands across the entire fleet simultaneously.

Security Best Practices: SSH keys are significantly more secure than passwords. A 2048-bit RSA key is nearly impossible to brute-force compared to a standard password.

Non-Interactive Execution: Automated backups, health checks, and deployments require "non-interactive" login. If a script pauses to ask for a password, the automation fails.

Audit Trail: By using specific keys for the thor user, we can track exactly which service or user initiated a change across the Stratos Datacenter.

Key Commands Used:

ssh-keygen -t rsa: Created the identity.

ssh-copy-id -i [path] [user]@[host]: Safely transferred the public key to the remote authorized_keys file.