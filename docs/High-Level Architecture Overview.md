# ☁️ High-Level Architecture Overview

This document provides a clear, high-level view of the **Smart Travel Booking Platform Cloud Deployment on Azure**.  
It describes how the system securely handles traffic flow, automates deployment, and ensures high availability and reliability using Azure cloud services and DevOps practices.

---

## 📌 **System Flow**

The system architecture is designed to handle user requests securely and efficiently from entry point to backend processing. Here’s how the end-to-end flow works:

1️⃣ **Client → Application Gateway**  
A user sends an **HTTPS** request to one of the custom domains configured for the platform (e.g., booking site or AI chatbot).

2️⃣ **SSL Termination & Routing**  
The **Azure Application Gateway** terminates the SSL connection, inspects the incoming request, and routes it to the correct backend based on the **multi-site configuration**.

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
This ensures that only authorized requests reach each component while keeping communication secure between the Application Gateway and backend VMs.

9️⃣ **Logging & Monitoring**  
The system uses **Azure built-in monitoring** and **activity logs** for full visibility into resource status and traffic flow.  
**Health probes**, performance metrics, and **automated alerts** ensure that any unhealthy backend services or performance bottlenecks are detected quickly, with instant notifications for troubleshooting.

---

## 🗺️ **Architecture Diagram**

Below is the high-level architecture diagram that visualizes the flow described above.

![Architecture Diagram](/diagrams/architecture-overview.png)

> **Note:** A more detailed breakdown of configurations, scripts, and any supporting screenshots is documented separately in their dedicated sections.

---

## ✅ **Key Components**

- **Azure Application Gateway**: Main reverse proxy that handles SSL termination, routing, multi-site configuration, health probes, and load balancing.
- **Virtual Machines (VMs)**: Host the backend applications and handle application logic processing.
- **Azure Blob Storage**: Serves static frontend assets for global users.
- **GitHub Actions CI/CD**: Automates builds and deployments for both frontend and backend services.
- **Virtual Networks, Subnets & NSGs**: Provide network isolation and secure traffic flow.
- **Azure Monitor & Alerts**: Ensure continuous performance tracking and automated issue notifications.

---

## 📚 **Where to Find Details**

Each part of this architecture is explained in detail in its own section:

- **Application Hosting:** VM setup and backend deployment flow.
- **CI/CD using GitHub Actions:** Complete pipelines with scripts.
- **Static Frontend Hosting:** Blob Storage setup and endpoint.
- **Application Gateway:** Full multi-host configuration and routing.
- **Network & Security:** VNet, subnets, NSGs structure.
- **Monitoring & Logging:** Built-in metrics, probes, and alerts.

Refer to the corresponding files for configuration snippets, visuals, and step-by-step explanations.

---

_Designed for secure, scalable, and fully automated cloud deployment._ 🚀
