## Day 16: High Availability - Nginx Load Balancer Deployment

### 📋 Project Objective
Implement a High Availability (HA) stack in Stratos DC by configuring an Nginx Load Balancer to distribute traffic across the application tier.

### ⚙️ Technical Specifications
- **LBR Host:** `stlb01`
- **Configuration Path:** `/etc/nginx/nginx.conf`
- **Backend Pool:** `stapp01`, `stapp02`, `stapp03`
- **Backend Port:** Discovered Apache listening on **8088**.

---

### 🛠️ Troubleshooting & Hurdles (The "Real World" Log)

#### 1. The "Missing Directory" Incident
**Issue:** Attempting to write the configuration using `tee` resulted in the error: `tee: /etc/nginx/nginx.conf: No such file or directory`.
**Root Cause:** The `nginx` package was not yet installed on the target LBR node. In CentOS/RHEL, the `/etc/nginx` directory is created as part of the RPM package installation process.
**Resolution:** Provisioned the `epel-release` repository and installed the `nginx` package before attempting configuration injection.

#### 2. Hostname/User Context Confusion
**Issue:** Errors encountered when attempting to run `systemctl` commands from the Jump Host targeting `thor@stapp01`.
**Root Cause:** SSH defaults to the current session user (`thor`). However, the App Servers require server-specific accounts (`tony`, `steve`, `banner`).
**Resolution:** Pivoted to specific SSH strings (e.g., `ssh tony@stapp01`) and manually restarted the `httpd` services on each node to ensure Requirement (C) was met.

#### 3. Backend Port Discovery
**Issue:** Initial configuration attempts failed to reach backends.
**Root Cause:** Standard web ports (80/8080) were not in use. 
**Resolution:** Executed `sudo ss -tunlp | grep httpd` on the application tier to identify that the dev team had bound Apache to a non-standard port: **8088**.

---

### ✅ Final Verification
```text
$ curl -I http://stlb01
HTTP/1.1 200 OK
Server: nginx/1.20.1
Connection: keep-alive