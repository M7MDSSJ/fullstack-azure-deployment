# 🖥️ Application Hosting on Azure VM

This section describes how the backend applications are deployed and hosted on a dedicated **Azure Virtual Machine (VM)** to ensure performance, flexibility, and full control over runtime configurations.

---

## 📌 **VM Setup**

- **Azure VM SKU:** `Standard_B1ms`  
  Chosen for its balance between cost-effectiveness and enough CPU/RAM for moderate backend workloads.
- **OS:** (e.g., Ubuntu 22.04 LTS) *(update if needed)*  
- The VM hosts both backend applications and acts as the core processing unit for booking operations and chatbot services.

> **Note:** Each backend runs under **PM2** as a process manager to ensure zero downtime and easy restarts.

✅ **VM Configuration (Azure Portal)**  
Shows the VM type, region, public IP, and networking details.

![VM Config](../screenshots/vm-config.png)

---

## ⚙️ **Backend Applications**

### 1️⃣ **Booking Application**

- **Domain:** [https://sky-shifters.duckdns.org/](https://sky-shifters.duckdns.org/)
- **Port:** `3000`
- **Role:** Handles all booking-related operations including flight search, reservations, and transaction processing.

✅ **PM2 Status (Booking App)**  
Shows the Booking App running under PM2.

![PM2 Booking](../screenshots/pm2-booking.png)

✅ **Listening Port**  
Confirms the Booking App listens on port `3000`.

![Booking Port](../screenshots/booking-port.png)

---

### 2️⃣ **Chatbot Application**

- **Domain:** [https://chatbot-sky-shifters.duckdns.org/](https://chatbot-sky-shifters.duckdns.org/)
- **Port:** `8001`
- **Role:** Provides AI-powered customer support and assists users with booking management through natural language conversation.

✅ **PM2 Status (Chatbot App)**  
Shows the Chatbot App running under PM2.

![PM2 Chatbot](../screenshots/pm2-chatbot.png)

✅ **Listening Port**  
Confirms the Chatbot App listens on port `8001`.

![Chatbot Port](../screenshots/chatbot-port.png)

---

## 🌐 **Domain Name Setup (DuckDNS)**

To make the backend services accessible and easily routable, we configured **DuckDNS**:
- Assigns each VM public IP a recognizable domain.
- Used later in **Application Gateway** multi-site routing to direct requests based on the requested service.
- Allows the frontend to request backend APIs using these custom subdomains.

✅ **DuckDNS Configuration Example**

![DuckDNS Config](../screenshots/duckdns-config.png)

---

## 🔗 **Next**

👉 This backend hosting setup works in tandem with:
- The **Nginx Reverse Proxy** configuration on the VM *(if applicable)*.
- The **Application Gateway Reverse Proxy** for secure multi-site SSL termination and routing.
- The **CI/CD pipelines** that automatically deploy code updates to the VM.

---

_This configuration ensures secure, stable, and flexible hosting for core backend services._ 🚀
