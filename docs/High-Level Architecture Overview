# ☁️ High-Level Architecture Overview

This document provides a clear, high-level view of the **Smart Travel Booking Platform Cloud Deployment on Azure**.  
It describes how the system securely handles traffic flow, automates deployment, and ensures high availability and reliability using Azure cloud services and DevOps practices.

---

## 📌 **System Flow**

The system architecture is designed to handle user requests securely and efficiently from entry point to backend processing. Here’s how the end-to-end flow works:

1️⃣ **Client → Application Gateway**  
A user sends an **HTTPS** request to one of the custom domains configured for the platform (e.g., booking site or AI chatbot).

2️⃣ **SSL Termination & Routing**  
The **Azure Application Gateway** terminates the SSL connection, inspects the incoming request, and routes it based on the **multi-site configuration** (multi-domain support).

3️⃣ **Health Probe**  
Before forwarding requests, the gateway performs real-time **health checks** on backend applications via dedicated `/health` endpoints to ensure they’re running properly.

4️⃣ **Backend Pool → VM**  
Healthy requests are forwarded through **internal HTTP** to the correct backend VM on its specific port.

5️⃣ **Backend Processing**  
The backend applications (booking API, AI chatbot) process the request and send a secure response back through the same flow.

6️⃣ **Static Frontend Hosting**  
Static website assets are served directly from **Azure Blob Storage**, providing high availability, global distribution, and reduced latency for frontend resources.

7️⃣ **CI/CD Pipeline**  
**GitHub Actions pipelines** automatically pull, build, and deploy the latest backend and frontend versions whenever code updates are pushed. This guarantees continuous integration and deployment with minimal manual work.

8️⃣ **Secure Networking**  
All traffic flow is protected through:
   - Isolated **Virtual Networks (VNets)**  
   - Segmented **subnets**  
   - Strict **Network Security Groups (NSGs)**  
This ensures that only authorized requests reach each component while keeping communication secure between Application Gateway and backend VMs.

9️⃣ **Logging & Monitoring**  
The system uses **Azure built-in monitoring** and **activity logs** for full visibility into resource status and traffic flow.  
**Health probes**, performance metrics, and **automated alerts** ensure that any unhealthy backend services or performance bottlenecks are detected quickly, with instant notifications for troubleshooting.

---

## 🗺️ **Architecture Diagram**

Below is the high-level architecture diagram that visualizes the flow described above.

![Architecture Diagram](./diagrams/architecture-overview.png)

> **Tip:** Replace `architecture-overview.png` with your final diagram file name. Make sure it clearly shows:
> - Clients
> - Application Gateway
> - SSL Termination
> - Health Probe
> - Backend Pools → VMs
> - Static Blob Storage
> - VNets, Subnets, NSGs
> - CI/CD Pipelines flow
> - Monitoring and Alerts

---

## ✅ **Key Components**

- **Azure Application Gateway**: Handles SSL termination, routing, health probes, and load balancing.
- **Virtual Machines (VMs)**: Host the backend applications with NGINX reverse proxy for routing and SSL offloading.
- **Azure Blob Storage**: Serves static frontend assets.
- **GitHub Actions CI/CD**: Automates builds and deployments.
- **Virtual Networks, Subnets & NSGs**: Provide network isolation and secure traffic flow.
- **Azure Monitor & Alerts**: Ensure continuous performance tracking and automated issue notifications.

---

## 🗂️ Next Steps

👉 For detailed configurations and step-by-step setups, check:
- [Application Hosting (VM)](./docs/Application-Hosting.md)
- [CI/CD using GitHub Actions](./docs/CI-CD.md)
- [Static Frontend Hosting](./docs/Static-Frontend-Hosting.md)
- [Nginx Reverse Proxy (on VM)](./docs/Nginx-Reverse-Proxy.md)
- [Application Gateway Reverse Proxy](./docs/Application-Gateway.md)
- [Network & Security](./docs/Network-Security.md)
- [Monitoring & Logging](./docs/Monitoring-Logging.md)

---

_Designed with reliability, security, and scalability in mind._ 🚀
