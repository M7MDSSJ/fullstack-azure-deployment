# 🏗️ Infrastructure as Code (IaC)

To ensure that the entire production environment is **repeatable**, **scalable**, and **easy to manage**, the team implemented the **Infrastructure as Code (IaC)** approach.

With IaC:
- All cloud resources — including **Virtual Machines**, **Application Gateway**, **Blob Storage**, **Network Security Groups (NSGs)**, **Virtual Networks (VNets)**, and **Subnets** — are defined and managed through **code files** instead of manual configurations in the Azure Portal.

---

## ✅ **How IaC Helps**

### 1️⃣ **Consistency & Repeatability**
- Every configuration is written in code, ensuring that deploying a new environment always produces the **same result**.
- Reduces human error and eliminates configuration drift between environments.

---

### 2️⃣ **Easy Redeployment & Scaling**
- If the team needs to rebuild the entire infrastructure in a new region or for a new customer, it’s **just one command away**.
- Adding new resources or updating existing configurations is simple and fully tracked in **version control**.

---

### 3️⃣ **Better Collaboration**
- The IaC files are stored in a **dedicated GitHub repository**, allowing the DevOps team to **collaborate** on infrastructure changes just like application code.
- All changes can be peer-reviewed through pull requests and rollbacks are quick if needed.

---

## 📁 **Where to Find the Code**

The complete Infrastructure as Code files are available here:
[`deployment-scripts/azure-iac/main.bicep`](../deployment-scripts/azure-iac/main.bicep) *(or main.tf if using Terraform)*

---

## 🛡️ **Benefits Achieved**

✔ **Same infrastructure every time.**  
✔ **Faster disaster recovery and testing new regions.**  
✔ **Secure, versioned, and documented.**

---

_For more details on the resulting architecture, see [High-Level Architecture](./ARCHITECTURE.md)._  
_For network and security best practices, see [Networking & Security](./Network-Security.md)._

