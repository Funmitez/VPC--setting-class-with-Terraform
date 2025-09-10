# VPC with EC2 Deployment (Terraform)

This project creates a **VPC** with public & private subnets, attaches an Internet Gateway, and deploys an **EC2 instance** in the public subnet.

## Features
- VPC with CIDR `10.0.0.0/16`
- Public & private subnets
- Internet Gateway + route table
- Security group allowing SSH (22) & HTTP (80)
- EC2 instance in public subnet

