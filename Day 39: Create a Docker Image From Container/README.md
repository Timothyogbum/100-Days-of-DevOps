Lab Report: Docker Image Lifecycle Management
## Objective
Create a persistent backup of a developer's modified container environment on Application Server 2.

## Technical Resolution Path
The project involved the following successful steps:

Host Discovery: Attempted to locate the container on stapp03, but docker ps -a confirmed the host was empty.

Environment Migration: SSH'd into stapp02 (172.16.238.11), where the target container was correctly identified.

State Capture: Identified the running container ubuntu_latest (ID: a6c7dee1eab0).

Image Creation: Executed docker commit to generate the official:devops image from the running container's writable layer.

Validation: Confirmed the new image (ID: 596a8f95da3e) is present in the local repository and approximately 58MB larger than the base ubuntu image, indicating saved changes.

## Final Verification
Entity,Name/ID,Status
Source Container,ubuntu_latest,Up 3 minutes
New Image,official:devops,Created (596a8f95da3e)
Host,stapp02,Verified