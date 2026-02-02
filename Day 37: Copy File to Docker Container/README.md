📄 Project README: Secure Container Data Transfer
Project: Confidential Data Migration

Target: App Server 3 (stapp03)

Container: ubuntu_latest

Status: ✅ Verified & Integrity Confirmed

1. 🏗️ Operation Overview
The task required moving an encrypted GPG file from the host filesystem into a running Docker container. Security protocols mandated that the file remain identical (bit-for-bit) after the transfer.

Source Path: /tmp/nautilus.txt.gpg (on host)

Destination Path: /tmp/ (inside ubuntu_latest)

Transport Method: docker cp

2. 🛠️ Technical Execution Log
Host Verification: Confirmed source file size (105 bytes) and initial MD5 hash.

Transfer: Utilized the native Docker CLI to stream the file into the container namespace.

Integrity Audit: Executed a checksum within the container environment to validate against the host's primary hash.

3. ✅ Integrity Verification Results
Location,MD5 Checksum,Status
Host (stapp03),23f68f2b440a3e72d32037d0a93d17bd,✅ Source
Container (ubuntu_latest),23f68f2b440a3e72d32037d0a93d17bd,✅ Match

