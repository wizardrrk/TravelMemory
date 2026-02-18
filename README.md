---
# NOTE:: All the applicaiton images are present in the images folder with proper naming at each stage those are taken for meaningful understanding.

https://copilot.microsoft.com/th/id/BCO.e15bf208-134f-4753-ad20-8ff66c200aee.png
<img width="1302" height="821" alt="image" src="https://github.com/user-attachments/assets/8edaa905-3cf5-41bf-9b35-ea92e2628ac4" />

# 🌍 TravelMemory – AWS Cloud Deployment

A full-stack **MERN application** deployed on **AWS EC2** with **MongoDB Atlas**, **Cloudflare DNS**, **SSL certificates**, and advanced **AWS services** like **Load Balancer**, **Auto Scaling Groups**, and **ACM certificates**. This project demonstrates end-to-end deployment of a scalable, secure web application.

---

## 🚀 Features
- **Frontend**: React-based UI for entering and viewing travel memories.
- **Backend**: Node.js + Express API connected to MongoDB Atlas.
- **Database**: MongoDB Atlas cluster with secure credentials.
- **Deployment**: AWS EC2 instances with Nginx reverse proxy.
- **DNS Management**: Namecheap domain onboarded to Cloudflare.
- **SSL Security**: HTTPS enabled via Certbot certificates.
- **Scalability**: Auto Scaling Groups with AMIs and Launch Templates.
- **Resilience**: Application Load Balancer with ACM certificates.

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
- **Network Access**:  
  ```
  0.0.0.0/0   # Allow public access (for demo only, restrict in production)
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
  git clone https://github.com/wizardrrk/TravelMemory.git
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
2. Onboard domain to Cloudflare → update nameservers in Namecheap.  
3. Wait ~30 minutes for propagation → status becomes **Active**.

---

### III. Deployment (Public IP – HTTP)
- Launch **EC2 instances** for frontend and backend.  
- Install Node.js, npm, clone repos, configure `.env`, and run servers.  
- Use **PM2** to manage processes in the background.  

---

### IV. Reverse Proxy with Nginx
- Configure Nginx to route traffic from port `80` → app ports (`3000`, `3001`).  
- Allows access without specifying ports in the URL.  

---

### V. Deployment with DNS (HTTP)
- Add DNS records in Cloudflare:  
  ```
  A   api.wizardrrk.store    <Backend_IP>
  A   www.wizardrrk.store    <Frontend_IP>
  A   wizardrrk.store        <Frontend_IP>
  ```
- Update Nginx configs to accept traffic from DNS names.  

---

### VI. Deployment with DNS + SSL (HTTPS)
- Install **Certbot** and enable SSL for both frontend and backend.  
- Update Nginx configs with SSL certificates.  
- Update frontend `.env` to use secure backend URL:  
  ```
  REACT_APP_BACKEND_URL=https://api.wizardrrk.store
  ```
- Access securely via:  
  - `https://wizardrrk.store`  
  - `https://www.wizardrrk.store`  
  - `https://api.wizardrrk.store`  

---

### VII. Advanced AWS Services – Scalability & Resilience
#### A) Auto Scaling
- Create **AMI images** from existing EC2 instances.  
- Build **Launch Templates** for frontend and backend.  

#### B) Target Groups
- Create target groups for EC2 instances.  
- Configure protocol: **HTTPS (443)**.  

#### C) ACM Certificates
- Issue Amazon Certificate Manager (ACM) certificates.  
- Example ARN:  
  ```
  arn:aws:acm:ap-south-1:223776318759:certificate/83bc4ade-c811-4eca-b7a4-23cad1babec5
  ```

#### D) Load Balancer
- Create **Application Load Balancer (ALB)**.  
- Attach target groups and ACM certificates.  
- Configure listeners for HTTPS traffic.  

#### E) Cloudflare Integration
- Add CNAME records for Load Balancer DNS.  
- Example:  
  ```
  CNAME   lb.wizardrrk.store   travel-memory-frontend-lb-962924110.ap-south-1.elb.amazonaws.com
  ```

- Access via:  
  ```
  https://lb.wizardrrk.store
  ```

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
- **Cloud**: AWS EC2, ALB, Auto Scaling Groups, ACM  
- **DNS**: Namecheap + Cloudflare  
- **SSL**: Certbot + ACM  



## 👨‍💻 Author
**Rajeev** – Passionate about cloud deployment, scalable architectures, and secure web applications.  

---
