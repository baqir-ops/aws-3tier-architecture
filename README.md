🚀 AWS 3-Tier Architecture Project (VPC + ALB + CloudFront)
📌 Project Overview

This project demonstrates the design and implementation of a secure and scalable 3-tier architecture on AWS, following real-world cloud best practices.
It focuses on network isolation, traffic routing, and high availability, rather than just application hosting.

The architecture separates:

Frontend layer (public access)

Application layer (private, protected)

Database layer (private, isolated)

This project was built as a hands-on cloud engineering lab to showcase AWS networking, load balancing, and security concepts.

🏗️ Architecture Diagram (Logical)
User
 │
 │  HTTPS
 ▼
CloudFront (CDN)
 │
 ▼
Application Load Balancer (Public Subnets)
 │
 ▼
Backend EC2 Instances (Private App Subnets)
 │
 ▼
Database Layer (Private DB Subnets)
## 📸 Project Screenshots
### VPC & Subnets
![VPC](screenshots/Screenshot%202026-01-07%20120313.png)

### Application Load Balancer
![ALB](screenshots/Screenshot%202026-01-12%20123111.png)

### Target Group & EC2
![EC2](screenshots/Screenshot%202026-01-13%20130517.png)

🧩 AWS Services Used

Amazon VPC

Public & Private Subnets (Multi-AZ)

Internet Gateway

Security Groups

Application Load Balancer (ALB)

Target Groups

Amazon EC2 (Amazon Linux 2023)

AWS Systems Manager (Session Manager)

Amazon CloudFront

🔐 Networking & Security Design

ALB deployed in public subnets

Backend EC2 deployed in private subnets

Database subnets isolated from public access

Security Groups used instead of open CIDR rules:

ALB SG allows HTTP (80) from internet

Backend SG allows traffic only from ALB SG

No direct SSH access (managed via SSM Session Manager)

⚙️ Load Balancing

Application Load Balancer (ALB)

Listener: HTTP : 80

Target Group:

Type: Instance

Protocol: HTTP

Port: 80

Health checks configured on backend instances

🌍 Content Delivery

CloudFront distribution configured in front of the ALB

Improves performance and simulates real-world frontend delivery

Supports HTTP/1.1 and HTTP/2

🧪 Testing & Validation

Verified ALB DNS resolution

Verified CloudFront distribution creation

Validated security group traffic flow

Confirmed backend isolation from direct internet access

Troubleshot package installation and connectivity issues

⚠️ Known Limitation (Intentional Design Choice)

The backend EC2 instances are deployed in private subnets without a NAT Gateway.

Impact:

Backend instances do not have outbound internet access

Package installation (e.g., dnf install httpd) fails due to no NAT

Reason:

This was a deliberate architectural decision to demonstrate:

Proper private subnet isolation

Real-world cloud security design

Understanding of NAT Gateway requirements

Improvement (Future Enhancement):

Add a NAT Gateway in a public subnet

Allow secure outbound access for updates while keeping instances private

💼 Skills Demonstrated

AWS VPC design (public vs private subnets)

Load balancing with ALB & target groups

Secure traffic flow using Security Groups

CloudFront integration

Troubleshooting AWS networking issues

Using AWS Systems Manager instead of SSH

Cost awareness and architectural trade-offs

🎯 Use Case

This project is designed as a portfolio-grade AWS lab suitable for:

Junior Cloud Engineer

AWS Support Engineer

DevOps / SRE (entry-level)

Cloud Operations roles

📌 Author

Muhammad Baqir Nawaz
Aspiring Cloud / AWS Engineer
Focused on hands-on projects, troubleshooting, and real-world architectures.

📎 Next Improvements

Add NAT Gateway for outbound access

Add Auto Scaling Group for backend tier

Add HTTPS listener with ACM certificate


Add CloudWatch alarms and logging
