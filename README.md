---
# NOTE: all the screenshots are attached in the images folder

# 🌍 TravelMemory – AWS Cloud Deployment

A full-stack **MERN application** deployed on **AWS EC2** with **MongoDB Atlas**, **Cloudflare DNS**, and **SSL integration**. This project demonstrates end-to-end deployment of a scalable, secure web application.

---

## 🚀 Features
- **Frontend**: React-based UI for entering and viewing travel memories.
- **Backend**: Node.js + Express API connected to MongoDB Atlas.
- **Database**: MongoDB Atlas cluster with secure credentials.
- **Deployment**: AWS EC2 instances with Nginx reverse proxy.
- **DNS Management**: Namecheap domain onboarded to Cloudflare.
- **SSL Security**: HTTPS enabled via Certbot certificates.

---

## 📦 Preparation Steps

### 1. MongoDB Atlas Setup
- **Cluster Name**: `herovired1`  
- **Database**: `travelmemorydb`  
- **Collection**: `travelmemorycollection`  
- **Connection String**:  
  ```
  mongodb+srv://mongo2026:Mongo2026@herovired1.9au5tmp.mongodb.net/travelmemorydb
  ```

### 2. Domain & DNS
- Purchased via **Namecheap**  
- Domain: `wizardrrk.store`  
- Managed through **Cloudflare** for DNS routing.

### 3. SSL Certificates
- Generated using **Certbot** based on DNS records.

---

## ⚙️ Implementation Steps

### I. Code Management
- Clone repository locally:
  ```
  git clone <your-repo-url>
  ```
- Configure `.env` files:
  - **Frontend**:
    ```
    REACT_APP_BACKEND_URL=http://127.0.0.1:3001
    ```
  - **Backend**:
    ```
    PORT=3001
    MONGO_URI=mongodb+srv://mongo2026:Mongo2026@herovired1.9au5tmp.mongodb.net/travelmemorydb
    ```
- Push updates to GitHub with default branch set to `master`.

---

### II. DNS & Cloudflare Setup
1. Buy/register domain (`wizardrrk.store`) via Namecheap.  
2. Onboard domain to Cloudflare:
   - Add domain → copy Cloudflare nameservers.  
   - Update nameservers in Namecheap → Custom DNS.  
3. Wait ~30 minutes for propagation → status becomes **Active**.

---

### III. Deployment Stages
1. **Frontend & Backend with Public IP (HTTP)** – WIP  
2. **Frontend & Backend with DNS (HTTP)** – WIP  
3. **Frontend & Backend with DNS + SSL (HTTPS)** – Secure deployment  

---

## 📂 Project Structure
```
TravelMemory/
│── frontend/        # React UI
│── backend/         # Express API
│── .env             # Environment configs
│── nginx.conf       # Reverse proxy setup
│── docs/            # Deployment guides
```

---

## 🔒 Security Best Practices
- Restrict MongoDB access to trusted IPs.  
- Use HTTPS for all traffic.  
- Manage DNS via Cloudflare for resilience.  
- Keep secrets in `.env` files, never commit them.  

---

## 🛠️ Tech Stack
- **Frontend**: React  
- **Backend**: Node.js, Express  
- **Database**: MongoDB Atlas  
- **Cloud**: AWS EC2  
- **DNS**: Namecheap + Cloudflare  
- **SSL**: Certbot  

---

## 📖 Future Enhancements
- Auto Scaling Groups for backend.  
- Load Balancer integration with ACM certificates.  
- CI/CD pipeline for automated deployments.  

---

## 👨‍💻 Author
**RAJEEV** – Passionate about cloud deployment, scalable architectures, and secure web applications.  

---
