# 🏗️ Infrastructure as Code (IaC)

To keep the production environment **repeatable** and **easy to rebuild**, the whole Azure setup was exported and organized as **Infrastructure as Code (IaC)**.

In this project:
- All core resources (**VM, Application Gateway, Blob Storage, VNet, Subnets, NSGs**) are defined as code.
- This means the same setup can be deployed again anytime without manual clicks in the Azure Portal.
- The IaC files are versioned in the repo, so any change is tracked, and the team can collaborate on infra updates.

---

## ✅ How It Fits This Project

- 🗂️ If the platform needs to run in a **new region**, it’s just `az deployment` (or `terraform apply`).
- ⚙️ When adding new services or scaling, infra changes stay **consistent** with no manual drift.
- 🔐 The code is stored under:  
  [`deployment-scripts/azure-iac/`](../deployment-scripts/azure-iac/)

---

## 📁 Example Resources Covered

- **Virtual Network & Subnets**: To isolate traffic between AGW and the VM.
- **NSGs**: To control allowed ports for AGW and backend.
- **Application Gateway**: Includes multi-site config and SSL cert bindings.
- **Blob Storage**: For static website hosting.
- **VM**: Runs backend apps with PM2.

---

_This keeps the full cloud deployment clear, trackable, and easy to redeploy._ 🚀
