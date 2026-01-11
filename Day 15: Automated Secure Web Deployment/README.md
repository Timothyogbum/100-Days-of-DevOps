## Day 15: Automated Secure Web Deployment
**Objective:** Deploy Nginx with SSL on App Server 1 using non-interactive automation.

**Key Achievements:**
- **Zero-Touch Config:** Avoided manual text editors by utilizing `tee` and `sed` for configuration injection.
- **SSL Hardening:** Correctly provisioned self-signed certs to `/etc/pki/tls/` and configured port 443 listeners.
- **Modularity:** Implemented custom server blocks via `conf.d/ssl.conf` rather than bloating the main `nginx.conf`.

**Validation:**
Verified via `curl -Ik`. Response confirmed `200 OK` over encrypted tunnel.