# TASK 5: Setting Up Harbor Registry

This project involves deploying **Harbor**, an open-source, enterprise-grade container registry, to create a secure and scalable alternative to Docker Hub for managing container images.

Harbor allows DevOps teams to host Docker images privately, with advanced features like:

- Role-based access control  
- Vulnerability scanning  
- Integration with CI/CD tools  
- Authentication systems such as LDAP  

Unlike Docker Hub, Harbor removes limitations like image pull rate limits and storage caps, giving teams full control over how and where their container images are stored and accessed. 

For DevOps engineers, this setup:

- Enhances security  
- Improves pipeline efficiency  
- Supports better infrastructure management by centralizing image distribution within a controlled, self-hosted environment

---

## Docker Compose and YAML

**Docker Compose** is a tool used to define and manage multi-container Docker applications.

**YAML** is a simple, human-readable way to write down settings or instructions, often used in DevOps to configure tools and environments.

Docker Compose uses YAML files to define and run multi-container applications—so instead of starting each service (e.g., web server, database, or cache) manually, everything is written in one file and launched with a single command.

### Benefits for DevOps:

- Automates environment setup  
- Ensures consistency across systems  
- Simplifies testing and deployment  
- Makes configurations easy to share, version, and update  

---

## Steps to Set Up Harbor:

1. Update and upgrade system packages  
2. Install Docker  
3. Install Docker Compose  
4. Download Harbor installer  
5. Extract Harbor package  
6. Copy and edit Harbor configuration  
7. Modify hostname and admin password in `harbor.yml`  
8. Install and start Harbor  
9. Access Harbor UI via browser  
10. Login using `admin` and your configured password  
11. Create a new project  
12. Login to Harbor via Docker CLI  
13. Push/pull images from the registry  
14. *(Optional)* Configure HTTPS with SSL certs  

---

## Run the `install_harbor.sh` Script

```bash
chmod +x install_harbor.sh
./install_harbor.sh
