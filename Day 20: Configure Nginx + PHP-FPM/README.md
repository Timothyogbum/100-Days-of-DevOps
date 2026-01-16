# Day 20: The LEMP Migration Challenge (stapp02)

## 🎯 Project Objective
Deploy a modern PHP 8.2 application environment using Nginx as a reverse proxy on port 8096, utilizing Unix Sockets for performance.

## 🛠️ The Technical Struggle & Resolutions

### 1. The OS Version Trap (EL7 vs EL9)
- **Problem:** Attempted to use legacy Remi repositories (EL7), resulting in `404` mirror errors and dependency conflicts.
- **Resolution:** Pivoted to the modern **EL9 DNF Module Stream** system.
- **Command:** `sudo dnf module enable php:8.2 -y`

### 2. The Permission "Ghost" (Unix Sockets)
- **Problem:** The Unix socket at `/var/run/php-fpm/default.sock` initially had `root` ownership, which would block Nginx from communicating with the PHP engine.
- **Resolution:** Configured `listen.owner` and `listen.group` to `nginx` within `www.conf` and set `listen.mode` to `0660`.



### 3. Configuration Shadowing
- **Problem:** Nginx returned 404 because a default listener in the main `nginx.conf` was overriding the new site configuration.
- **Resolution:** Cleaned the global `nginx.conf` and used `sudo tee` to create a dedicated application file in `/etc/nginx/conf.d/`.

## 💡 Engineering Reflection
This task highlighted the importance of **Environment Awareness**. A script that works on CentOS 7 will fail on EL9. Mastering `dnf modules` and `Unix Domain Sockets` allows for a more secure, lower-latency stack than traditional TCP-based PHP processing.

## ✅ Final State
- **URL:** http://stapp02:8096/index.php
- **Payload:** "Welcome to xFusionCorp Industries!"
- **PHP Version:** 8.2.x (Verified)