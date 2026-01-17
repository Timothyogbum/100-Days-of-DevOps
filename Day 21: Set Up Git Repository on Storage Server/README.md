# Day 21: Git Infrastructure Provisioning (Storage Server)

## 🎯 Project Objective
Establish a centralized version control hub on the Stratos DC Storage Server to provide a secure, persistent location for the Nautilus development team's code.

## 🛠️ Technical Implementation

### 1. Tooling Installation
Installed the Git engine on the RedHat-based Storage Server using the YUM package manager to ensure compatibility with system libraries.
- **Host:** Storage Server
- **Command:** `sudo yum install -y git`

### 2. Bare Repository Initialization
Initialized the `/opt/beta.git` repository using the `--bare` flag.
- **Path:** `/opt/beta.git`
- **Logic:** Unlike a standard repository, a **bare repository** does not have a working directory. This architecture is required for central "push" servers to prevent conflicts between the remote state and locally checked-out files.



### 3. File System Structure
The resulting directory contains the essential Git metadata required for collaboration:
- `hooks/`: For automation scripts.
- `objects/`: The compressed data storage.
- `refs/`: To track branches and tags.



## 💡 Engineering Reflection: Storage Reliability
By hosting the Git repository on the **Storage Server** rather than an application server, we leverage the infrastructure's dedicated storage arrays. This ensures that even if an application server is replaced or scaled, the source code history remains intact and accessible via the internal network.

## ✅ Final Status
Verified the directory structure of `/opt/beta.git`. The repository is ready to be added as a `remote` for developer workstations.