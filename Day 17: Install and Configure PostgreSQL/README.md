## Day 17: PostgreSQL Data Tier Provisioning

### 📋 Project Objective
Initialize a secure backend database environment for a new application deployment in Stratos DC, ensuring specific user isolation and permission scoping.

### ⚙️ Implementation Details
- **User:** `kodekloud_aim` (Identified in `\du` role list)
- **Database:** `kodekloud_db2` (Identified in `\l` database list)
- **Permissions:** Verified `CTc` (Connect, Temporary, Create) privileges granted to `kodekloud_aim`.

### ✅ Verification Audit
The following metadata was captured directly from the PostgreSQL 13.14 console:

```text
Role name     | Attributes
--------------+-----------
kodekloud_aim | 

Name          | Access privileges
--------------+---------------------------------------
kodekloud_db2 | kodekloud_aim=CTc/postgres

🧠 Lessons Learned
Granular Permissions: By granting permissions specifically on kodekloud_db2, we ensure the kodekloud_aim user cannot interfere with system databases or other application data.

Session Contexts: Managed the entire workflow through sudo -u postgres, demonstrating the ability to handle administrative tasks without needing to log in directly as a root-level system user.