Day 8: Provisioning the Ansible Control Node
The Mission: Install Ansible version 4.10.0 globally on the Jump Host to act as the central orchestration point for the Stratos Datacenter.

The "Why" - Why is this setup critical?
Version Pining (Stability): In DevOps, we use specific versions (like 4.10.0) instead of just "latest." This ensures that automation scripts remain predictable and don't break due to unexpected updates in the Ansible core or modules.

Global Accessibility: By installing to /usr/local/bin using sudo pip3, we ensure the ansible binary is in the system-wide $PATH. This allows any authorized sysadmin on the Jump Host to run automation tasks, regardless of their individual user environment.

The "Control Node" Pattern: Ansible is agentless. By designating the Jump Host as the "Control Node" and leveraging the SSH keys we set up on Day 7, we can now manage the entire fleet without needing to install additional software on the target App Servers.

Technical Verification:
Binary Location: /usr/local/bin/ansible
Core Version: 2.11.12
Python Version: 3.9.18