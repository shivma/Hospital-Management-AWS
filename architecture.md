# AWS Architecture – Hospital Management System (HIPAA-Aligned)

## Overview
This project implements a HIPAA-aligned cloud architecture for a Hospital Management Web Application using Amazon Web Services (AWS). The system is designed to securely handle sensitive healthcare data (PHI) by following network isolation, least privilege access, and secure traffic flow principles.

The architecture ensures that only the Application Load Balancer (ALB) is internet-facing, while application servers and the database remain fully isolated in private subnets.

---

## High-Level Architecture
- One Virtual Private Cloud (VPC): `10.0.0.0/16`
- Internet Gateway attached to the VPC
- Public and private subnets distributed across multiple Availability Zones
- Internet-facing Application Load Balancer
- Private EC2 application server
- Private Amazon RDS database
- Bastion Host for secure administrative access

---

## Network Design

### VPC
- CIDR: `10.0.0.0/16`
- Provides isolated networking for the hospital application

### Public Subnets
- `10.0.1.0/24` (AZ-1a)
- `10.0.2.0/24` (AZ-1b)

Resources:
- Application Load Balancer (ALB)
- Bastion Host

Routing:
- Public Route Table
- Route: `0.0.0.0/0 → Internet Gateway`

---

### Private Subnets

#### Application Subnet
- `10.0.3.0/24`
- Contains EC2 App Server running:
  - React frontend
  - Node.js backend

#### Database Subnet
- `10.0.4.0/24`
- Contains Amazon RDS (MySQL/PostgreSQL)
- No public accessibility

Routing:
- Private Route Table
- Internal routing only (No route to IGW)

---

## Traffic Flow
1. Users access the application via the Internet.
2. Internet traffic reaches the Application Load Balancer (ALB).
3. ALB forwards requests to the EC2 Application Server in the private subnet.
4. The application server communicates with Amazon RDS for database operations.
5. Administrative SSH access is allowed only through the Bastion Host.

---

## Security & HIPAA Alignment

This architecture follows HIPAA-style security best practices:

### Network Security
- No direct internet access to EC2 or RDS
- Private subnets used for sensitive resources
- Bastion Host for controlled SSH access

### Access Control
- Security Groups enforce least privilege
- Database access restricted to application server only

### Data Protection
- RDS encryption at rest (AWS-managed keys)
- TLS encryption in transit (ALB → EC2)

### Monitoring & Audit (Conceptual)
- CloudWatch for logs and metrics
- VPC Flow Logs for network visibility

---

## Conclusion
This architecture provides a secure and scalable foundation for a hospital management system by following AWS best practices and HIPAA-aligned security principles. It is suitable for real-world healthcare applications where data confidentiality, integrity, and controlled access are critical.
