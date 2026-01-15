# Day 18: Distributed LAMP Stack for xFusionCorp WordPress Migration

## 🎯 Project Objective
Deploy a highly available LAMP (Linux, Apache, MySQL, PHP) environment within the Stratos Datacenter. The architecture requires a decoupled web and database layer with shared storage to support a scalable WordPress installation.

## 🏗️ Architecture Overview
- **Web Layer:** Triple-redundant Apache cluster (stapp01, stapp02, stapp03).
- **Storage Layer:** Shared NFS mount at `/var/www/html` for application code persistence.
- **Database Layer:** Centralized MariaDB server (stdb01) with remote access enabled.



## 🛠️ Technical Implementation

### 1. Web Layer Configuration (Apache & PHP)
On all app hosts, I automated the port reconfiguration and installed the necessary PHP-MySQL connectors.
- **Port Migration:** Used `sed` to programmatically update the `Listen` directive from 80 to `5001`.
- **Command:** `sudo sed -i 's/^Listen 80/Listen 5001/g' /etc/httpd/conf/httpd.conf`
- **Dependencies:** Installed `httpd`, `php`, and `php-mysqlnd`.

### 2. Database Layer Configuration (MariaDB)
On the DB server, I provisioned the relational backend and established secure remote credentials.
- **Service Hardening:** Utilized `sudo mysql` to bypass `unix_socket` authentication for initial setup.
- **SQL Logic:**
  - Created database: `kodekloud_db10`
  - Created user: `kodekloud_rin` with wildcard host (`%`) access.
  - Password: `GyQkFRVNr3`
- **Networking:** Verified `bind-address` was set to `0.0.0.0` to allow ingress from the app subnet.



### 3. Verification & Connectivity
- **Web Check:** Confirmed Apache listening on `5001` via `grep`.
- **Integration Check:** Triggered the LBR validation script, confirming the PHP application successfully established a handshake with the MariaDB backend using the `kodekloud_rin` service account.

## 💡 Engineering Insights
- **Scalability:** By offloading the database and using shared storage, we can add `stapp04` or `stapp05` instantly without data migration.
- **Troubleshooting:** Resolved the `Access denied for user 'root'@'localhost'` error by identifying the `unix_socket` plugin and using elevated system privileges for database administration.

## ✅ Final Result
- **Status:** Production-Ready
- **Connectivity Message:** "App is able to connect to the database using user kodekloud_rin"