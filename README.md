# 🚀 Terraform Project – VPC with Public/Private Subnets + EC2

![Terraform](https://img.shields.io/badge/Terraform-v1.8+-623CE4?logo=terraform&logoColor=white)  
![AWS](https://img.shields.io/badge/AWS-VPC%20%7C%20EC2%20%7C%20Subnets-FF9900?logo=amazon-aws&logoColor=white)  
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 📖 Project Overview
This project provisions an **AWS Virtual Private Cloud (VPC)** with one public subnet and one private subnet.  
An **EC2 instance** is deployed inside the public subnet with an attached security group that allows SSH and HTTP access.  

This is a **portfolio project** showcasing Terraform skills in **infrastructure as code (IaC)**, **networking**, and **cloud automation**.

---

## 🛠️ Features
- ✅ Custom VPC (`10.0.0.0/16`)  
- ✅ Public and private subnets across AZs  
- ✅ Internet Gateway + route table for public subnet  
- ✅ Security group with SSH (22) + HTTP (80) access  
- ✅ Ubuntu EC2 instance deployed in the public subnet  
- ✅ Outputs: VPC ID, Subnet ID, and EC2 Public IP  

---

## 📂 Project Structure
```
vpc-ec2-project/
│── main.tf
│── variables.tf
│── outputs.tf
│── provider.tf
│── terraform.tfvars (excluded via .gitignore)
│── README.md
│── .gitignore
```

---

## ⚙️ Prerequisites
- [Terraform](https://developer.hashicorp.com/terraform/downloads) v1.3+  
- [AWS CLI](https://aws.amazon.com/cli/) configured with valid credentials  
- An existing **AWS key pair** (e.g., `linux-keypair2.pem`)  

---

## 🚀 Usage
1. Clone the repo:
   ```bash
   git clone https://github.com/<your-username>/terraform-vpc-ec2.git
   cd terraform-vpc-ec2
   ```

2. Initialize Terraform:
   ```bash
   terraform init
   ```

3. Plan the deployment:
   ```bash
   terraform plan
   ```

4. Apply the configuration:
   ```bash
   terraform apply
   ```

5. Get the EC2 public IP:
   ```bash
   terraform output ec2_public_ip
   ```

6. SSH into your instance:
   ```bash
   ssh -i linux-keypair2.pem ubuntu@<EC2_PUBLIC_IP>
   ```

---

## 📊 Diagram

Here’s the high-level architecture:

```
             +--------------------+
             |     AWS VPC        |
             |   (10.0.0.0/16)    |
             +----------+---------+
                        |
          +-------------+-------------+
          |                           |
  Public Subnet (10.0.1.0/24)   Private Subnet (10.0.2.0/24)
          |                           |
     +----+-----+                     |
     |  EC2 VM  |                     |
     | (Ubuntu) |                     |
     +----------+                     |
          |                           |
   Internet Gateway                   |
          |                           |
     Accessible via SSH/HTTP          |
```

---

## 📷 Screenshots

| Resource | Screenshot |
|----------|------------|
| EC2 Instance | ![EC2 Screenshot](screenshots/ec2-instance.png) |
| VPC Overview | ![VPC Screenshot](screenshots/vpc-overview.png) |
| Subnets | ![Subnets Screenshot](screenshots/subnets.png) |

*(You can upload AWS Console screenshots into a `screenshots/` folder in your repo and they’ll appear here.)*

---

## 🔑 Variables
The main variables are defined in `variables.tf`:

| Variable          | Description                 | Default     |
|-------------------|-----------------------------|-------------|
| `aws_region`      | AWS region to deploy        | `us-east-1` |
| `vpc_cidr`        | VPC CIDR block              | `10.0.0.0/16` |
| `public_subnet_cidr` | CIDR for public subnet   | `10.0.1.0/24` |
| `private_subnet_cidr`| CIDR for private subnet  | `10.0.2.0/24` |
| `instance_type`   | EC2 instance type           | `t2.micro`  |
| `key_name`        | AWS key pair for SSH        | — (required) |

---

## 📝 Notes
- The EC2 instance is deployed using the latest **Ubuntu 22.04 LTS AMI** (AMI ID may vary by region).  
- The `terraform.tfvars` file (excluded from GitHub) stores your personal values, e.g.:

  ```hcl
  aws_region = "us-east-1"
  key_name   = "linux-keypair2"
  ```

---

## 📜 License
This project is licensed under the MIT License — feel free to use and adapt for your own portfolio.
