# 🚀 CI/CD Pipeline for Backend Applications

This document outlines the Continuous Integration and Continuous Deployment (CI/CD) process used to automate deployment for both backend applications of the Smart Travel Booking platform:

- **Booking Application** (`smart-air-port`)
- **Chatbot Application** (`Flight_chatbot`)

CI/CD is implemented using **GitHub Actions**, allowing fast, secure, and reliable updates to backend code directly on the Azure Virtual Machine.

---

## 📌 Overview of the Process

For both applications, a **GitHub Actions workflow** is triggered on each push to the `main` branch.

The CI/CD pipeline follows these steps:

1. **Connect to Azure VM via SSH** using encrypted credentials stored in GitHub Secrets.
2. **Pull the latest code** from the GitHub repository.
3. **Build or compile** the application using its appropriate runtime.
4. **Restart the application** using **PM2** to apply the new code with zero downtime.

✅ This ensures fast, repeatable, and fully automated deployments with no need for manual access to the VM.

---

## 🔐 Secrets Management

To ensure secure access to the VM and avoid hardcoding sensitive information:
- The SSH `host`, `username`, and `private key` are stored in **GitHub Repository Secrets**.
- For the **Chatbot Application**, additional API credentials are also stored in Secrets and injected dynamically at deployment time (explained below).

Secrets used include:
- `HOST`
- `USERNAME`
- `KEY`
- `AMADEUS_API_KEY`, `GROQ_API_KEY`, `GEMINI_API_KEY`, `BASE_URL`, etc.

---

## 📦 Booking Application CI/CD

- **Repository:** [`smart-air-port`](https://github.com/Aliexe-code/smart-air-port)
- **Workflow Script:** [`deployment-scripts/deploy-booking.yml`](../deployment-scripts/deploy-booking.yml)
- **Key Runtime:** `bun`

### 🧩 Summary of Steps:
- SSH into the VM.
- Pull latest code.
- Run `bun install` and `bun build`.
- Restart the application using `pm2`.

📸 **Example Run Screenshot:**

![Booking Workflow Run](../screenshots/booking-workflow.png)

---

## 🤖 Chatbot Application CI/CD

- **Repository:** [`Flight_chatbot`](https://github.com/Mohammed973-ai/Flight_chatbot)
- **Workflow Script:** [`deployment-scripts/deploy-chatbot.yml`](../deployment-scripts/deploy-chatbot.yml)
- **Key Runtime:** `Python + Uvicorn`

### 🧩 Summary of Steps:
- SSH into the VM.
- Pull latest code.
- **Dynamically generate the `.env` file** using secrets from the GitHub repository.
- Install dependencies using pip.
- Start the server using Uvicorn through a generated `start.sh` script.
- Manage the app lifecycle using `pm2`.

📸 **Example Run Screenshot:**

![Chatbot Workflow Run](../screenshots/chatbot-workflow.png)

---

## 📄 Dynamic `.env` Creation (Chatbot Only)

To keep credentials secure and prevent hardcoding sensitive data into the codebase:
- The `.env` file is **not included in the repository**.
- Instead, it is created dynamically during deployment using values from the **GitHub Secrets**.
  
This approach provides several advantages:
- ✅ No manual editing required on the VM.
- ✅ Prevents accidental exposure of credentials in the GitHub repo.
- ✅ Easy to update API keys (just update the GitHub Secret).

Example from the script:
```bash
cat <<EOF > .env
AMADEUS_API_KEY=${{ secrets.AMADEUS_API_KEY }}
AMADEUS_API_SECRET=${{ secrets.AMADEUS_API_SECRET }}
BASE_URL=${{ secrets.BASE_URL }}
GROQ_API_KEY=${{ secrets.GROQ_API_KEY }}
GEMINI_API_KEY=${{ secrets.GEMINI_API_KEY }}
EOF
```
This .env file is then used by the Python application during runtime.

----

## ✅ Benefits of This Setup

🔄 Fully automated deployment triggered by a simple git push.

🛡️ Secrets are managed securely and not exposed in code.

🕒 Fast turnaround from commit to production.

📉 Reduces human error and manual deployment delays.

🔧 Easy to maintain, update, and scale.
