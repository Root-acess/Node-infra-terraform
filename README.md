# Node.js Application Deployment on AWS using Terraform

This project automates the deployment of a scalable and secure **Node.js application** on AWS using **Terraform**. The architecture is designed for high availability, monitoring, and alerting using AWS managed services.

---

## Architecture Overview

The deployment uses the following AWS components:

### Frontend (FE) Layer
- **ACM (AWS Certificate Manager)**: Provides SSL/TLS certificates for secure communication.
- **Route 53**: Manages DNS routing for the application.
- **AWS WAF (Web Application Firewall)**: Protects against common web exploits.
- **CloudFront (CF)**: CDN for caching and improving performance.
- **Application Load Balancer (ALB)**: Distributes incoming traffic across frontend EC2 instances.
- **Frontend Auto Scaling Group (FE ASG)**: Manages frontend EC2 instances dynamically based on demand.
- **S3 Bucket**: Used for storing static assets (e.g., images, logs, configuration).

---

### Backend (BE) Layer
- **Network Load Balancer (NLB)**: Routes traffic to backend EC2 instances securely.
- **Backend Auto Scaling Group (BE ASG)**: Manages backend EC2 instances running the Node.js application.
- **Lifecycle Hooks & Scheduling**: Used for instance lifecycle management (e.g., warmup, graceful shutdown).

---

### Database Layer
- **RDS (MySQL)**: Centralized relational database for application data.

---

### Monitoring & Alerts
- **CloudWatch Log Group (CW Log Group)**: Collects logs from EC2 instances (`/log` directory).
- **Metric Filters & CloudWatch Alarms**: Monitors log patterns and triggers alarms based on specific metrics.
- **SNS Topic & Lambda Function**: Sends notifications (e.g., error alerts) via Slack or email.

---

## Deployment Flow

1. **Terraform Initialization**
   ```bash
   terraform init
```
