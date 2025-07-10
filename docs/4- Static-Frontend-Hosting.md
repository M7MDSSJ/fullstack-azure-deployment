# 🌐 Static Frontend Hosting using Azure Blob Storage

To serve the static frontend files globally with high availability and minimal cost, the project uses **Azure Blob Storage** with the **Static Website Hosting** feature enabled.

---

## 📌 **How It Works**

1️⃣ **Build the Frontend**  
After developing and testing the frontend application locally, a **production build** is generated.  
This produces the final static files:  
- HTML  
- CSS  
- JavaScript  
- Assets (images, fonts, etc.)

✅ **Example Build Files in Blob Container:**  
The final build files are uploaded to a dedicated **Blob Storage container**.

![Frontend Files in Blob Container](/screenshots/container-content.png)

---

2️⃣ **Enable Static Website Hosting**

In the Azure Blob Storage account:
- Static website hosting is enabled.
- An **index document** (e.g., `index.html`) and an optional error document (`404.html`) are defined.
- Azure automatically provisions a **public endpoint URL** to access the website.

✅ **Website Endpoint URL Example:**  
The live frontend for this project is accessible at:  
[https://taier.z6.web.core.windows.net/](https://taier.z6.web.core.windows.net/)

![Blob Storage Endpoint](/screenshots/endpoint.png)

---

## ⚡ **Why Use Blob Storage for Static Hosting?**

✅ **Simplicity**  
No need to configure or maintain servers — just upload your files, set the access level, and it’s ready.

✅ **Cost-effectiveness**  
Much cheaper than serving static assets through a VM or App Service. You only pay for storage and minimal bandwidth.

✅ **Performance**  
Static content is delivered directly via Azure’s globally distributed edge network — ensuring low latency and fast loading times for all users worldwide.

✅ **Scalability**  
No matter how many visitors the website has, Blob Storage automatically scales to handle the traffic.

---

## 🔗 **How It Fits in the Architecture**

- This setup **offloads static asset delivery** from the backend VM, which remains focused on processing dynamic API requests.
- It complements the **Application Gateway** that handles routing for dynamic traffic, while static content is served directly and independently.
- The frontend calls the backend services (e.g., Booking and Chatbot APIs) using the custom domains managed via DuckDNS and routed through the Application Gateway.

---

_This simple yet powerful setup provides a modern, efficient way to serve static websites at scale._ 🚀

