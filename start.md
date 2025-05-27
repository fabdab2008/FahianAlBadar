# 🚀 Getting Started with DevOps

DevOps is a set of practices that bridges software development and IT operations, with the goal of shortening the development lifecycle and delivering high-quality software continuously.

---

## 🔧 What is DevOps?

- Combines **Development** and **Operations**
- Focuses on automation, collaboration, and monitoring
- Popular tools: Git, Docker, Jenkins, Kubernetes

---

## 🧰 Key Concepts

### 1. CI/CD (Continuous Integration/Continuous Deployment)
- Automate building, testing, and deploying code
- Helps reduce errors and speed up delivery

### 2. Infrastructure as Code (IaC)
- Manage servers and environments with code
- Tools: Terraform, Ansible, AWS CloudFormation

---

## 📦 Example: Simple CI Workflow

```yaml
# .github/workflows/deploy.yml
name: Deploy
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run tests
        run: echo "Running tests..."
