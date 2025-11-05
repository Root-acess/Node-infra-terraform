# 🌐 NodeApp-Infrastructure

This repository contains the **Terraform Infrastructure as Code (IaC)** setup for deploying a **Node.js application** on AWS.  
It follows a modular structure to ensure scalability, security, and maintainability across multiple environments.

---

## 🚀 Overview

The infrastructure automates the deployment of both **frontend and backend** components for a Node.js application using AWS services.  
It supports **load balancing, auto-scaling, monitoring, and notifications** — all defined as reusable Terraform modules.

### 🔧 Key AWS Components

| Layer | Service | Purpose |
|-------|----------|----------|
| **Networking** | VPC, Subnets, Security Groups | Core network and access configuration |
| **Load Balancing** | ALB, NLB | Distributes traffic between frontend & backend EC2s |
| **Compute** | EC2 (ASG) | Runs the Node.js app with scaling policies |
| **Storage** | S3 | Stores app artifacts or backups |
| **Monitoring** | CloudWatch | Centralized logging and alerting |
| **Automation** | Lambda, SNS | Notifications and remediation tasks |
| **Edge Security** | CloudFront, WAF, ACM | Secure global content delivery |
| **Database** | RDS (MySQL/PostgreSQL) | Persistent data storage for the app |

---

## 🧩 Folder Structure

```

NodeApp-Infrastructure/
├── environments/
│   └── development/        # Environment-specific configurations
├── localmodules/           # Modular Terraform components
│   ├── alb/
│   ├── asg/
│   │   └── include/        # Templates, SSH keys, user data
│   ├── cloudfront/
│   ├── cloudwatch/
│   ├── lambda/
│   │   └── files/          # Python scripts or Lambda packages
│   ├── nlb/
│   ├── rds/
│   ├── sns/
│   └── vpc/
├── scripts/                # Deployment or automation scripts
└── docs/                   # Documentation, architecture diagrams, notes

````

---

## ⚙️ Usage

### 1. Clone the Repository

```bash
git clone https://github.com/<your-org>/NodeApp-Infrastructure.git
cd NodeApp-Infrastructure
````

### 2. Initialize Terraform

```bash
terraform init
```

### 3. Validate Configuration

```bash
terraform validate
```

### 4. Plan and Apply

```bash
terraform plan -var-file=environments/development/terraform.tfvars
terraform apply -var-file=environments/development/terraform.tfvars
```

---

## 🌍 Environments

* **development** – Testing and dev workloads
* *(You can add more like `staging/` or `production/` as needed)*

---

## 🧠 Design Principles

* **Modular Architecture:** Each AWS component is an independent Terraform module.
* **Reusability:** Modules can be reused across multiple environments.
* **Security First:** Uses WAF, ACM, and IAM best practices.
* **Scalability:** ASG and Load Balancers ensure high availability.
* **Automation:** Lambda and SNS handle monitoring and alerting.

---

## 🪄 Future Enhancements

* Add CI/CD pipelines for automated Terraform deployment
* Add module testing via `terratest`
* Add cost monitoring and optimization scripts
* Add staging and production environments

---

## 👥 Maintainers

**Project Owner:** Charon (Hiralal Singh)
**GitHub:** [Root-acess](https://github.com/Root-acess)

---

## 🧾 License

This project is licensed under the **MIT License** – feel free to use and modify as needed.

---
