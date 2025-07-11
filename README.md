# ✈️ Full-Stack Application Cloud Deployment Using Azure

This repository documents the **end-to-end production deployment** of the Smart Travel Booking Platform — a full-stack project running on **Azure Cloud**, with everything from VM hosting, static frontend, reverse proxies, CI/CD pipelines, secure networking, and Infrastructure as Code.

---

## 📌 What’s Inside

This repo includes:
- ✅ **High-Level Architecture** — how all components fit together.
- ✅ **Backend Hosting** — details for the VM setup running both backend applications.
- ✅ **Static Frontend Hosting** — served globally via Azure Blob Storage.
- ✅ **Nginx Reverse Proxy** (Dev) — initial local routing and SSL with Let’s Encrypt.
- ✅ **Application Gateway (Production)** — Layer 7 reverse proxy with SSL termination and multi-site routing.
- ✅ **Networking & Security** — VNet, Subnets, and NSGs design.
- ✅ **Monitoring & Logging** — using Azure Monitor, Activity Logs, and Alerts.
- ✅ **Infrastructure as Code (IaC)** — exported templates for redeployment.
- ✅ **Cost Estimation** — daily and monthly cost overview.

---

## 🗺️ **Project Overview**

- **Platform:** Full-stack Smart Travel Booking System (Booking + Chatbot).
- **Backend:** Hosted on a dedicated Azure VM with PM2.
- **Frontend:** Built with Flutter, hosted as static files in Blob Storage.
- **Reverse Proxy:**  
  - Dev: Local NGINX with SSL via Let’s Encrypt.  
  - Prod: Azure Application Gateway with multi-site config.
- **CI/CD:** GitHub Actions pipelines for automated pull, build, and redeploy.
- **Security:** Virtual Network with isolated subnets and strict NSGs.
- **Monitoring:** Azure Monitor, Activity Logs, and Alerts for real-time status and incidents.
- **IaC:** Full environment exported as reusable JSON template via Azure CLI.

---

## ⚙️ **Key Resources**

| Component          | Purpose                                               |
|--------------------|-------------------------------------------------------|
| **VM**             | Hosts backend apps: Booking & Chatbot                 |
| **Application Gateway** | Reverse proxy, SSL termination, multi-site routing |
| **Blob Storage**   | Static web hosting for the frontend                   |
| **VNet & Subnets** | Isolate components and control traffic flow           |
| **NSGs**           | Define strict inbound/outbound rules                  |
| **CI/CD Pipelines**| Auto-deploy code updates via GitHub Actions           |
| **Monitoring**     | Metrics, logs, and alerts for fast troubleshooting    |
| **IaC Template**   | Rebuild infra anywhere, anytime                       |

---

## 🗂️ **Documentation**

🔗 [🗺️ Architecture Overview](./docs/ARCHITECTURE.md)  
🔗 [🖥️ Application Hosting](./docs/Application-Hosting.md)  
🔗 [📦 Static Frontend Hosting](./docs/Static-Frontend-Hosting.md)  
🔗 [🔄 Nginx Reverse Proxy (Dev)](./docs/Nginx-Reverse-Proxy.md)  
🔗 [☁️ Application Gateway Reverse Proxy](./docs/Application-Gateway.md)  
🔗 [🔐 Networking & Security](./docs/Network-Security.md)  
🔗 [📊 Monitoring & Logging](./docs/Monitoring-Logging.md)  
🔗 [🏗️ Infrastructure as Code (IaC)](./docs/Infrastructure-as-Code.md)  
🔗 [💰 Cost Estimation](./docs/Cost-Estimation.md)  
🔗 [🚀 CI/CD Deployment](./docs/CI-CD-Deployment.md)

---

## 🏷️ **Estimated Cost**

- **Daily:** ~$1.93 USD
- **Monthly:** ~$58 USD

> ⚡ This includes the VM, AGW, Blob Storage, data transfer, and monitoring.

---

## ✅ **How to Use This Repo**

1. Check each doc for full config details.
2. Use the provided IaC template to redeploy in a new region if needed.
3. Follow the CI/CD pipelines to keep apps updated automatically.

---

## 🛡️ **Notes**

- All secrets are handled securely via GitHub Secrets and not committed.
- Certificates are managed through Let’s Encrypt and uploaded to the AGW.
- All configs, probes, and NSG rules follow the **least privilege** principle.

---

## ✨ **About This Project**

Developed as part of a graduation project to build a **cloud-ready**, secure, and production-grade deployment for a full-stack Smart Travel Booking Platform.

---

_Ready to deploy, monitor, and scale._ 🚀
