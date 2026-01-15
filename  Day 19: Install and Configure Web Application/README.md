# Day 19: Apache Multi-Site Configuration & Path Mapping

## 🎯 Objective
Configure a single Apache (httpd) instance to serve two distinct static websites using directory-based context paths on a custom port (8087).

## 🛠️ Technical Implementation

### 1. Custom Port Configuration
To comply with the infrastructure requirements of the Stratos Datacenter, I migrated the Apache listener from the default port 80 to 8087.

sudo sed -i 's/^Listen 80/Listen 8087/g' /etc/httpd/conf/httpd.conf
sudo systemctl restart httpd

2. Path-Based Routing
Instead of using complex VirtualHosts with different domain names, I implemented path-based routing by organizing the content within the DocumentRoot.

Beta Site: Deployed to /var/www/html/beta/

Apps Site: Deployed to /var/www/html/apps/

3. Verification via CLI
Verified the availability of both sites using curl from the local application server:

Beta Site Response:

HTML

<h1>KodeKloud</h1>
<p>This is a sample page for our beta website</p>
Apps Site Response:

HTML

<h1>KodeKloud</h1>
<p>This is a sample page for our apps website</p>
💡 Engineering Insight: Context Paths vs. VirtualHosts
Using context paths (/beta/, /apps/) is an efficient way to host multiple internal tools or "in-progress" projects under a single IP/Domain. It simplifies SSL certificate management (one cert for the domain) and reduces DNS complexity compared to using subdomains for every small project.

✅ Final Status: SUCCESS
Port: 8087

Beta Link: http://localhost:8087/beta/

Apps Link: http://localhost:8087/apps/