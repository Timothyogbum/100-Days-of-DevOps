Lab Report: Docker Image Management
## Objective
Perform container image lifecycle operations on App Server 1 in the Stratos DC, specifically pulling a specific distribution of BusyBox and re-tagging it for local development use.

## Implementation Details
Host: App Server 1 (stapp01)

Original Image: busybox:musl (Pulled from Docker Hub)

New Tag: busybox:local

## Steps Executed
### 1. Image Retrieval
Pull the official musl variant of BusyBox. This variant is specifically optimized for size and static linking.
sudo docker pull busybox:musl

### 2. Image Re-Tagging
Created a local alias for the image. This allows internal scripts or developers to reference a consistent tag (local) even if the underlying base image version changes in the future.
sudo docker tag busybox:musl busybox:local

### 3. Verification
The local image cache was inspected to ensure the tag was successfully applied and linked to the correct Image ID.
sudo docker images

## Technical Findings
Image ID Match: Both repositories (busybox) and tags (local, musl) point to ID 0188a8de47ca.

Efficiency: Docker tagging is a metadata operation and does not consume additional disk space (both entries total 1.51MB).

Permissions: Elevated privileges (sudo) were required for Docker socket interaction on stapp01.
