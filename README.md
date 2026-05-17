# 🚀 AWS Custom VPC & Docker Deployment Project

This project demonstrates how to build a secure, custom network infrastructure on AWS from scratch and deploy a containerized 3-Tier web application using Docker Compose. 

Instead of using AWS default settings, I configured the entire network manually to understand cloud networking and environment isolation.

---

## 🏗️ What I Built (Architecture)
The system is divided into a secure network setup and an application setup:

* **Custom VPC (`10.0.0.0/16`):** My own isolated virtual network space on AWS.
* **Public Subnet (`10.0.1.0/24`):** Where my web server (EC2) lives so people can access it.
* **Private Subnet (`10.0.2.0/24`):** Reserved for the database (MySQL) to keep it safe from the public internet.
* **Internet Gateway (IGW):** Connected to the Route Table to allow internet traffic into the Public Subnet.
* **Security Groups:** Configured firewall rules to allow SSH (Port 22) for management and Web Traffic (Port 9000).

---

## 🛠️ Tech Stack
* **Cloud Infrastructure:** AWS (VPC, EC2, IGW, Route Tables, Security Groups)
* **Containerization:** Docker & Docker Compose v2
* **Backend:** Python 3.9 & Flask API
* **Database:** MySQL 8.0 (Using Docker Volumes for data persistence)
* **OS:** Linux Ubuntu
<img width="1905" height="857" alt="image" src="https://github.com/user-attachments/assets/0ed34187-5087-4c35-8d0a-361f4c7f3558" />
<img width="1571" height="794" alt="image" src="https://github.com/user-attachments/assets/55d457ad-8ce1-40ef-941b-085087162d1e" />
<img width="1428" height="582" alt="image" src="https://github.com/user-attachments/assets/0ec20a0c-49d2-4a05-873c-296e38bdeed1" />
<img width="1185" height="901" alt="image" src="https://github.com/user-attachments/assets/93f8ca48-6af2-4b35-ac28-c1ef105da299" />
<img width="1919" height="913" alt="image" src="https://github.com/user-attachments/assets/64aba308-f64e-48c1-9aa2-dc62099fc99a" />



---

## 💡 Key Things I Learned & Solved

While building this project, I faced real-world deployment challenges and fixed them:

1. **Custom VPC Routing:** Learned that a subnet doesn't automatically get internet access. I had to manually attach an Internet Gateway and add a `0.0.0.0/0` route to the Route Table.
2. **Linux vs Windows File Permissions (`chmod 400`):** Encountered the "Unprotected Private Key File" error. I learned that running `chmod 400` inside a mounted Windows folder (`/mnt/c/Downloads`) fails silently. I fixed this by moving the `.pem` key into the native Linux home directory (`~`) where file permissions work correctly.
3. **Docker Socket Permissions:** Solved the `permission denied` error when running docker commands by managing user groups using `newgrp docker`, allowing me to run deployments without using unsafe `sudo` commands.

---

## 🚀 How to Deploy This Project

### 1. Prepare your SSH Key (In your local Linux/WSL terminal)
Move your AWS `.pem` key to your Linux home directory and set the right permissions:
```bash
