# Using containerd in DevOps

## Overview
`containerd` is a high-performance, industry-standard container runtime used for managing the lifecycle of containers. Originally a core component of Docker, it has evolved into a standalone project under the Cloud Native Computing Foundation (CNCF). It plays a vital role in modern DevOps workflows, particularly in container orchestration and automation pipelines.

## Use Cases in DevOps
- Running containers in CI/CD pipelines  
- Powering container orchestration with Kubernetes  
- Building scalable and secure microservices infrastructure  
- Hosting containers in cloud-native and edge computing environments  

## Conclusion
In DevOps settings, `containerd` is a foundational tool that enables efficient, secure, and scalable container operations. It is especially valuable when working with Kubernetes or building minimal, production-ready container infrastructure.

---

# USING `containerd` SEPARATELY

## Step 1: Check Existing containerd Installation
```bash
which containerd
containerd --version
```

## Step 2: Install Standalone containerd
```bash
sudo apt update
sudo apt install containerd

sudo systemctl enable containerd
sudo systemctl start containerd
```

## Step 3: Use containerd via `ctr` or `nerdctl`
```bash
curl -LO https://github.com/containerd/nerdctl/releases/download/v1.7.0/nerdctl-1.7.0-linux-amd64.tar.gz
tar xzvf nerdctl-1.7.0-linux-amd64.tar.gz
sudo mv nerdctl /usr/local/bin/

nerdctl run hello-world
```
