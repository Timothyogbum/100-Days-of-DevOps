## Day 13: Hardening Port 3002 across Nautilus Infrastructure
**Task:** Secure the website port by restricting access to the Load Balancer only.
**Solution:** - Deployment of `iptables` as the host-level firewall.
- Implementation of a "Whitelist-then-Deny" strategy for port 3002.
- Verified persistence on stapp01, stapp02, and stapp03.
**Result:** Successfully locked down port 3002 from unauthorized external access.