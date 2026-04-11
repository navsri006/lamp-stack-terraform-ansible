# ⚙️ LAMP Stack Auto-Deployment on AWS — Terraform + Ansible

Fully automated deployment of a LAMP stack (Linux, Apache, MySQL, PHP) on AWS EC2 using Terraform for infrastructure provisioning and Ansible for configuration management. One-command deployment from zero to a running web server on the cloud.

---

> **Terraform Plan Output — AWS Resources to be Created**
<img width="795" height="361" alt="Screenshot 2025-08-19 224044" src="https://github.com/user-attachments/assets/196330f7-d8b4-4905-a524-92a6ed79f3b0" />

---

> **AWS EC2 Instance Running — Console View**
![Uploading Screenshot 2025-08-18 214244.png…]()
<img width="1902" height="610" alt="Screenshot 2025-08-19 223934" src="https://github.com/user-attachments/assets/611cd73f-60de-49c5-98db-963075060530" />

---

> **Ansible Playbook Version — LAMP Stack Installed**
<img width="636" height="400" alt="Screenshot 2025-09-18 214715" src="https://github.com/user-attachments/assets/105b9714-ed3c-4f48-960a-1b52ccf1f10f" />

---

> **LAMP Stack Live — Apache Served via Public IP**
<img width="420" height="166" alt="Screenshot 2025-09-16 235013" src="https://github.com/user-attachments/assets/21547779-31cd-4897-ab06-408dd37d6143" />


---

> **LAMP Stack Deployed — Apache Served via Public IP**
<img width="1143" height="1172" alt="Screenshot 2025-09-17 143435" src="https://github.com/user-attachments/assets/f73d93b3-0efd-45aa-a31b-da0368bffd01" />

--- 


## 🏗️ Architecture Overview

```
<img width="636" height="400" alt="Screenshot 2025-09-18 214715" src="https://github.com/user-attachments/assets/105b9714-ed3c-4f48-960a-1b52ccf1f10f" />

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Cloud Provider | AWS (EC2, VPC, Security Groups, IAM) |
| Infrastructure as Code | Terraform |
| Configuration Management | Ansible |
| OS | Amazon Linux 2 / Ubuntu |
| Web Server | Apache HTTP Server |
| Database | MySQL / MariaDB |
| App Layer | PHP |

---

## ✅ What Was Automated

### Terraform — Infrastructure Provisioning
- Provisioned **EC2 instance** (Amazon Linux 2) with defined instance type
- Created and attached a **Security Group** allowing HTTP (80), HTTPS (443), SSH (22)
- Configured **IAM role** for EC2 with least-privilege permissions
- Outputted the EC2 **public IP** for use by Ansible
- All infrastructure defined as **reusable, version-controlled code**

### Ansible — Configuration Management
- Connected to the EC2 instance via SSH using key-based authentication
- Installed and started **Apache**, **MySQL**, and **PHP** automatically
- Deployed a sample PHP application to verify the full LAMP stack is operational
- Configured **MySQL** with a secure initial setup
- Ensured all configurations are **idempotent** — safe to run multiple times

---

## 🚀 How to Deploy

### Prerequisites
```bash
# Install required tools
terraform --version    # >= 1.0
ansible --version      # >= 2.9
aws configure          # Set your AWS credentials
```

### Deploy in 3 Steps
```bash
# Step 1 — Clone the repository
git clone https://github.com/navsri006/aws-lamp-stack-automation-ansible.git
cd aws-lamp-stack-automation-ansible

# Step 2 — Provision AWS infrastructure
cd terraform/
terraform init
terraform plan
terraform apply

# Step 3 — Configure LAMP stack on EC2
cd ../ansible/
ansible-playbook -i inventory/aws_ec2.yml site.yml

# Done! Access your LAMP stack at the EC2 public IP
```

### Teardown
```bash
cd terraform/
terraform destroy
```

---

## 📁 Project Structure

```
aws-lamp-stack-automation-ansible/
├── terraform/
│   ├── main.tf              # EC2 + Security Group resources
│   ├── variables.tf         # Input variables
│   ├── outputs.tf           # Public IP output
│   └── provider.tf          # AWS provider config
├── ansible/
│   ├── site.yml             # Master playbook
│   ├── inventory/
│   │   └── aws_ec2.yml      # Dynamic EC2 inventory
│   └── roles/
│       ├── apache/          # Apache installation + config
│       ├── mysql/           # MySQL installation + secure setup
│       └── php/             # PHP installation + app deployment
├── screenshots/
└── README.md
```

---

## 🔑 Key Skills Demonstrated

- Infrastructure as Code (IaC) with Terraform
- Cloud infrastructure provisioning on AWS
- Automated configuration management with Ansible
- Idempotent playbook design
- SSH key-based authentication for automation
- AWS IAM, EC2, Security Groups
- End-to-end DevOps deployment pipeline

---

## 🔮 Future Improvements

- Add CI/CD pipeline via GitHub Actions for automated deployment on push
- Replace self-signed SSL with Let's Encrypt certificate
- Use Terraform remote state (S3 backend) for team collaboration
- Add CloudWatch monitoring and alerting
- Implement auto-scaling group for production readiness

---

## 👤 Author

**Sriram Arumugam** — RHCE Certified | Junior DevOps Engineer  
[LinkedIn](https://linkedin.com/in/sriram-arumugam) | [GitHub](https://github.com/navsri006)
