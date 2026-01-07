**Objective:** Install and configure Apache Tomcat on App Server 2 (`stapp02`) to host a beta Java application on port 3000.

**Key Accomplishments:**
- **Installation:** Setup Java OpenJDK and Apache Tomcat 9 via `yum`.
- **Hardening/Config:** Modified `server.xml` to rebind the HTTP connector from port 8080 to 3000 using `sed`.
- **Deployment:** Deployed `ROOT.war` from the Jump Host to the Tomcat `webapps` directory to ensure the app is reachable at the context root.
- **Verification:** Successfully validated the deployment using `curl http://stapp02:3000`.

**Lessons Learned:**
- Commented-out XML blocks can mirror active ones after a global `sed` replacement, but they do not affect the server's runtime behavior.