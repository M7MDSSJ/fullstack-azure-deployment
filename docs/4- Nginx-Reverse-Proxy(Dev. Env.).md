# 🔄 Nginx Reverse Proxy on Azure VM (Development Phase)

During the **development environment** stage, an **Nginx Reverse Proxy** was configured directly on the Azure Virtual Machine (VM).  
This allowed the team to route incoming client requests to the correct backend applications and handle basic SSL termination before migrating to the **Azure Application Gateway** for production.

---

## 📌 **Purpose of NGINX in Dev**

- Manage routing for multiple backend applications hosted on the same VM.
- Bind each backend app to its own **custom DuckDNS domain**.
- Terminate SSL/TLS connections securely using **Let’s Encrypt Certbot**.
- Simulate real-world multi-host behavior in a simple, low-cost way before moving to a production-grade gateway.

---

## 🌐 **Domain-to-Backend Mapping**

Each backend app is mapped to its own domain:

| Application         | Domain URL                                   | Port  |
|---------------------|----------------------------------------------|-------|
| Booking Application | [https://sky-shifters.duckdns.org/](https://sky-shifters.duckdns.org/) | 3000  |
| Chatbot Application | [https://chatbot-sky-shifters.duckdns.org/](https://chatbot-sky-shifters.duckdns.org/) | 8001  |

✅ Requests arriving at each domain are forwarded internally by NGINX to the appropriate port.

---

## 🛠️ **How It Was Configured**

1️⃣ **Installed NGINX** on the VM (e.g., `sudo apt install nginx`).  
2️⃣ Created a separate **server block** for each application to define:
   - The `server_name` (domain).
   - Proxy settings to forward traffic to the local port.
   - SSL directives for HTTPS.
3️⃣ Issued free SSL certificates using **Certbot Let’s Encrypt**.
4️⃣ Reloaded NGINX to apply changes.

---

## 🔒 **SSL Certificates with Certbot**

- Used **Certbot** to automatically generate and renew SSL certificates for each DuckDNS domain.
- Ensured HTTPS connections for secure data transmission even during development.
- This helped mimic the final production security flow.

✅ Example:  
![Certbot Success](../screenshots/certbot-success.png)

---

## 📂 **Configuration Files**

The full NGINX configuration for both backend apps is stored here:  
[`deployment-scripts/nginx-config-booking.conf`](../deployment-scripts/nginx-config-booking.conf)  
[`deployment-scripts/nginx-config-chatbot.conf`](../deployment-scripts/nginx-config-chatbot.conf)

Check these files for:
- `server_name` definitions.
- Proxy settings (`proxy_pass`).
- SSL certificate paths (`/etc/letsencrypt/...`).

---

## 📸 **Verification Screenshots**

- ✅ **Nginx Running on VM:** Shows config file structure.  
  ![Nginx Config](../screenshots/nginx-config.png)

- ✅ **PM2 Processes:** Confirms backend apps are running on the correct ports.  
  ![PM2 Status](../screenshots/pm2-status.png)

- ✅ **Domains Accessible Over HTTPS:** Booking & Chatbot accessible via DuckDNS.

---

## 🗃️ **Transition to Production**

In the **production environment**, the role of SSL termination and routing was migrated to a fully managed **Azure Application Gateway**, which handles:
- Centralized SSL management.
- Multi-site configuration for multiple domains.
- Health probes and backend pools.
- Secure, scalable reverse proxy.

---

## ✅ **Key Takeaways**

- Using NGINX for development reverse proxy provided:
  - Quick local domain routing.
  - Secure HTTPS with Let’s Encrypt.
  - Easy troubleshooting and testing for multi-host flows.
- This setup made the transition to a production-ready **Application Gateway** smooth and predictable.

---

👉 For full production gateway details, see the dedicated doc: [Application Gateway Reverse Proxy](./Application-Gateway.md).

---
