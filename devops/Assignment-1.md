# ASSIGNMENT 1

## 1. Set Up Docker Environment
Run an NGINX container using Docker on your virtual machine.

## 2. Create a GitHub/GitLab Repository
Create a new private repository:
- Add a single `index.html` file that displays your personal details (name, ID, contact, etc.).
- Commit and push the file.

## 3. Pull HTML into NGINX Container
Clone your GitHub/GitLab repository inside your VM:
- Configure the NGINX container to serve your `index.html` by:
  - Mounting the cloned directory as a volume into the container at `/usr/share/nginx/html`.

## 4. Expose the Site
Make sure the site is exposed on port 80.
- Access the site using your browser (e.g., `http://<your-vm-ip>`).

---

## Workflow

### 1. Creating a Private Repo and Generating a PAT

### 2. Clone Repository
```bash
git init
git remote add origin https://github.com/fabdab2008/DevOps.git
git add Intro.html
git commit -m "Initial commit"
git push -u https://fabdab2008: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@github.com/fabdab2008/DevOps.git master
git clone https://github.com/fabdab2008/DevOps.git
```

### 3. Running NGINX Container Successfully
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

docker run --name my-nginx -d -p 80:80 nginx
```

### 4. Mounting HTML File in the Container
```bash
ls -l ~/DevOps
rm -rf ~/DevOps
git clone https://github.com/fabdab2008/DevOps.git
ls -l ~/DevOps

docker stop my-nginx
docker rm my-nginx

docker run --name my-nginx -d -p 80:80 \
  -v ~/DevOps:/usr/share/nginx/html \
  -v ~/nginx-custom/default.conf:/etc/nginx/conf.d/default.conf \
  nginx

curl http://localhost
```

---

## Summary

This task involved setting up a complete web server deployment pipeline using Docker and GitHub on a virtual machine environment. The goal was to serve a personal HTML page using the NGINX web server inside a Docker container. Below is a summary of the key steps and outcomes:

### Docker Environment Setup
Docker was installed and configured on an Ubuntu-based virtual machine. A container running the official NGINX image was launched, exposing port 80 to allow web access.

### Version Control with GitHub
A private GitHub repository named **DevOps** was created. It contained an `Intro.html` file with personal details such as name, ID, and contact. A Personal Access Token (PAT) was generated for secure authentication. The HTML file was committed and pushed to the remote repository using Git commands.

### Integrating GitHub with Docker (Volume Mounting)
The repository was cloned into the VM, and the `Intro.html` file was served by NGINX through volume mounting. This was done by binding the local project directory (`~/DevOps`) to the NGINX container’s web root directory (`/usr/share/nginx/html`). Additionally, a custom NGINX configuration file was mounted to enhance server behavior.

### Site Exposure and Testing
The site was exposed on port 80, making it accessible via a browser using the VM’s IP address. The `curl` command was used to verify that the server was correctly responding with the custom HTML content.
