📄 Project README: Nginx Container Deployment
Project: Docker Service Validation

Target: Application Server 2 (stapp02)

Status: ✅ Success / Running

1. 🏗️ Deployment Details
The Nautilus DevOps team required a lightweight web server instance for application testing. We utilized the Alpine Linux-based Nginx image to ensure a minimal resource footprint.

Server: stapp02.stratos.xfusioncorp.com

Container Name: nginx_2

Image: nginx:alpine

Runtime Mode: Detached (-d)

2. 🛠️ Execution Log
SSH Access: Authenticated as steve on stapp02.

Pull & Run: Executed docker run which automatically pulled the nginx:alpine image from Docker Hub.

Validation: Verified the container state via docker ps to ensure the entrypoint script initialized correctly.

3. ✅ Verification Evidence
# Command:
sudo docker ps -f "name=nginx_2"

# Output:
CONTAINER ID   IMAGE          STATUS          PORTS     NAMES
65207f839d9e   nginx:alpine   Up 16 seconds   80/tcp    nginx_2

