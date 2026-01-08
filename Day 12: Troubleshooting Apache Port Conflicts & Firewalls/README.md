## Day 12: Troubleshooting Apache Port Conflicts & Firewalls
**Problem:** App server `stapp01` unreachable on port 5003.
**Diagnosis:** - Port 5003 was occupied by `sendmail` on localhost.
- Apache was stopped.
- Firewall (iptables) was dropping packets ("No route to host").
**Fix:**
- Stopped `sendmail` service.
- Reconfigured Apache to `Listen 5003` using `sed`.
- Added `iptables` ACCEPT rule for port 5003.
**Result:** Service verified via `curl` from Jump Host.
EOF