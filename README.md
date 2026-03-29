# 🚀 AWS 3-Tier Architecture Deployment

### 👩‍💻 Developed by **Riya Kumari**

---

## 📌 Project Overview

This project demonstrates a **production-ready 3-tier architecture** deployed on AWS, following industry best practices for:

* ✅ High Availability
* ✅ Scalability
* ✅ Security

It simulates a real-world application using:

* Web Tier (Frontend)
* Application Tier (Backend - Node.js)
* Database Tier (Amazon RDS - MariaDB)

---

## 🧠 Architecture Diagram (Core Highlight)

<p align="center">
<img src="./application-code/architecture.webp" alt="AWS 3 Tier Architecture" width="900"/>
</p>

---

## 🔥 Architecture Flow

```
User → Route 53 → Application Load Balancer → Web Tier (Nginx)
     → App Tier (Node.js API) → RDS (MariaDB)
```

---

## 🏗️ Architecture Breakdown

### 🌐 1. Web Tier (Public Subnet)

* Application Load Balancer (ALB)
* Nginx Web Server
* Handles incoming traffic
* Routes requests to App Tier

---

### ⚙️ 2. Application Tier (Private Subnet)

* Node.js backend (PM2 managed)
* Handles business logic
* Connects to database securely

---

### 🗄️ 3. Database Tier (Private Subnet)

* Amazon RDS (MariaDB)
* Stores application data
* Not publicly accessible (secure)

---

## 🛠️ Tech Stack

* **Cloud**: AWS (EC2, ALB, RDS, S3, Route53)
* **Backend**: Node.js
* **Web Server**: Nginx
* **Database**: MariaDB (RDS)
* **Process Manager**: PM2

---

## ⚡ Deployment Steps

### 🔹 1. Launch EC2 Instances

* Create Web Tier instance
* Create App Tier instance
* Assign proper Security Groups

---

### 🔹 2. Setup Application Tier

```bash
cd app-tier
npm install
pm2 start index.js
```

Test:

```bash
curl http://localhost:4000/health
```

---

### 🔹 3. Setup Web Tier

```bash
cd web-tier
npm install
npm run build
```

Install Nginx:

```bash
sudo yum install nginx -y
```

---

### 🔹 4. Configure Nginx

```bash
cd /etc/nginx
sudo rm nginx.conf
```

Copy config from S3:

```bash
aws s3 cp s3://3tier-app-deployment-aws/nginx.conf .
```

Restart:

```bash
sudo systemctl restart nginx
```

---

### 🔹 5. Setup Load Balancer

* Create Application Load Balancer
* Use **Public Subnets**
* Add Listener → HTTP (80)

---

### 🔹 6. Create Target Group

* Target Type: Instance
* Protocol: HTTP
* Port: 4000
* Health Check Path:

```
/health
```

---

### 🔹 7. Attach EC2 to Target Group

* Register App Tier instance
* Wait until status = ✅ Healthy

---

### 🔹 8. Setup Route 53

* Create Hosted Zone
* Add A Record → ALB DNS

---

## 🔐 Security Best Practices

* Private subnets for App & DB
* Security Groups restrict traffic
* No public DB access

---

## 📸 Key Features

✔ Fully scalable architecture
✔ Load balanced traffic
✔ Secure DB layer
✔ Real-world deployment scenario

---

## 🎯 Project Impact

This project demonstrates:

* Real AWS infrastructure setup
* End-to-end deployment skills
* DevOps + Cloud engineering knowledge

👉 Ideal for:

* Final Year Projects
* DevOps Roles
* Cloud Engineer Positions

---

## ⭐ Resume Highlight

> Designed and deployed a **highly available 3-tier architecture on AWS** using EC2, ALB, RDS, and Nginx, implementing secure networking and scalable backend services.

---

## 📌 Author

**Riya Kumari**
🚀 Aspiring DevOps & Cloud Engineer

---

## 💡 Future Improvements

* CI/CD pipeline (GitHub Actions)
* Auto Scaling Groups
* HTTPS (SSL via ACM)
* Monitoring (CloudWatch)

---

⭐ If you like this project, give it a star!
