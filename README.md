# Hospital Management System – AWS (HIPAA-Aligned)

A full-stack Hospital Management Web Application designed with a **HIPAA-aligned AWS cloud architecture**.  
This project demonstrates secure handling of healthcare data using **private subnets, controlled access, and AWS best practices**.

---

## 📌 Project Overview

This project simulates a real-world hospital system where:
- Patient data is securely stored
- Doctors and appointments are managed through APIs
- The application follows **security-first cloud design**, inspired by HIPAA principles

The main goal of this project is to **showcase cloud architecture, backend engineering, and deployment readiness**, not just UI.

---

## 🏗️ Architecture Overview

- Single VPC (`10.0.0.0/16`)
- Internet-facing Application Load Balancer (ALB)
- Private EC2 App Server (React + Node.js)
- Private Amazon RDS database
- Bastion Host for secure SSH access
- No direct internet access to EC2 or RDS

📄 Detailed architecture is documented here:  
➡️ `architecture/architecture.md`

---

## 🔐 HIPAA-Aligned Security Design

This project follows **HIPAA-style security principles**:

- Network isolation using private subnets
- Least-privilege access via Security Groups
- Database fully isolated (no public access)
- Bastion Host for administrative access
- Environment variables for secrets management
- Designed for encryption at rest and in transit

> ⚠️ This is a **HIPAA-aligned educational project**, not a certified HIPAA-compliant system.

---

## 🛠️ Tech Stack

### Backend
- Node.js
- Express.js
- REST APIs
- MySQL (Amazon RDS ready)

### Frontend
- React.js

### Cloud & Networking
- AWS VPC
- EC2
- Application Load Balancer (ALB)
- Amazon RDS
- Internet Gateway
- Bastion Host

---

## 📂 Repository Structure
