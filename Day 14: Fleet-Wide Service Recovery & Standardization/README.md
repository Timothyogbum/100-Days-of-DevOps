## Day 14: Fleet-Wide Service Recovery & Standardization

**Objective:** Resolve Apache service unavailability and standardize the listener port to `5002` across three application nodes in a production environment.

**Executive Summary:**
Identified a critical service failure on `stapp01` caused by a port conflict with the `sendmail` daemon. Executed a fleet-wide configuration update to ensure all Apache instances were listening on port `5002` as per the new monitoring requirements.

**Technical Workflow:**
1. **Discovery:** Logged into the cluster and audited service status. `stapp01` reported `Active: failed`.
2. **Conflict Resolution:** Discovered `sendmail` binding to TCP 5002 on `stapp01`. Decommissioned the conflicting service and re-allocated the port to `httpd`.
3. **Configuration as Code:** Utilized `sed` stream editing to modify `/etc/httpd/conf/httpd.conf` listener directives across `stapp01`, `stapp02`, and `stapp03`.
4. **Validation:** Confirmed successful socket binding using `ss -tunlp` (socket statistics) across all nodes to ensure 100% compliance.

**Tools Used:** Bash, Systemd, Apache, Net-Tools, Iproute2 (ss), Sed.