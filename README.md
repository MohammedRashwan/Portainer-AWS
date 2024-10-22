# Portainer Deployment on AWS EC2

## Overview
Successfully deployed **Portainer**, a powerful management UI for Docker, on an Amazon EC2 instance to streamline container orchestration and management.

---

## Key Responsibilities
### 🛠 Infrastructure Setup
- **Launched an EC2 instance** with optimal configurations for container deployment.

### 🚀 Portainer Installation
- **Utilized Docker Compose** to deploy Portainer, enabling a user-friendly interface for managing Docker containers and images.

### 🔐 Security Configuration
- **Implemented AWS security group rules** to ensure secure access to the Portainer interface while adhering to best practices for network security.

### 👥 User Management
- **Configured role-based access control** in Portainer, allowing for secure multi-user access and management of containerized applications.

### 📊 Monitoring and Optimization
- **Monitored performance metrics** and optimized the deployment for improved reliability and efficiency.

---

## Impact
This project enhanced the team's ability to manage containerized applications efficiently, reducing deployment times and improving operational oversight.

---

## Deployment Steps

### Step 1: Infrastructure Setup

1. **Log in to AWS Management Console:**
   - Go to [AWS Management Console](https://aws.amazon.com/console/) and sign in.

2. **Launch an EC2 Instance:**
   - Navigate to **EC2** > **Instances** > **Launch Instances**.
   - Select the **Amazon Linux 2 AMI**.
   - Choose an instance type (e.g., `t2.micro`).
   - Configure instance details, storage, tags, and security groups.

3. **Configure Security Group:**
   - Add rules for:
     - **SSH (Port 22):** Your IP
     - **Portainer (Port 9000):** Anywhere (0.0.0.0/0 for testing)

---

### Step 2: Portainer Installation

1. **Connect to the EC2 Instance:**
   ```bash
   ssh -i your-key.pem ec2-user@your-public-dns
┌─────────────────────────────────────────┐
│               Install Docker            │
├─────────────────────────────────────────┤
│ 1. Update the package index:            │
│    sudo yum update -y                   │
│                                         │
│ 2. Install Docker:                      │
│    sudo amazon-linux-extras install     │
│    docker                               │
│                                         │
│ 3. Start the Docker service:            │
│    sudo service docker start             │
│                                         │
│ 4. Add the ec2-user to the Docker group:│
│    sudo usermod -a -G docker ec2-user   │
└─────────────────────────────────────────┘


┌─────────────────────────────────────────┐
│            Install Docker Compose       │
├─────────────────────────────────────────┤
│ 1. Download Docker Compose:             │
│    sudo curl -L "https://github.com/    │
│    docker/compose/releases/download/     │
│    1.29.2/docker-compose-$(uname -s)-   │
│    $(uname -m)" -o /usr/local/bin/      │
│    docker-compose                        │
│                                         │
│ 2. Apply executable permissions:        │
│    sudo chmod +x /usr/local/bin/docker-compose │
└─────────────────────────────────────────┘


mkdir portainer && cd portainer
nano docker-compose.yml


docker-compose up -d

┌─────────────────────────────────────────┐
│         Restrict Security Group Access  │
├─────────────────────────────────────────┤
│ 1. Go to the EC2 Dashboard in AWS.      │
│ 2. Select **Security Groups** from the   │
│    left menu.                           │
│ 3. Choose the security group associated  │
│    with your EC2 instance.               │
│ 4. Edit inbound rules to allow only      │
│    trusted IPs for Portainer on port 9000.│
└─────────────────────────────────────────┘


┌─────────────────────────────────────────┐
│             Access Portainer            │
├─────────────────────────────────────────┤
│ 1. Open a web browser and navigate to:  │
│    http://your-public-dns:9000          │
│ 2. Create an admin user by providing a   │
│    username and password.                │
└─────────────────────────────────────────┘


┌─────────────────────────────────────────┐
│        Configure Role-Based Access      │
├─────────────────────────────────────────┤
│ 1. After logging in, navigate to **Users**│
│    in Portainer.                         │
│ 2. Create additional users and assign    │
│    roles (Admin, Read-Only, etc.) based  │
│    on required permissions.               │
└─────────────────────────────────────────┘


┌─────────────────────────────────────────┐
│            Monitor Performance           │
├─────────────────────────────────────────┤
│ 1. Use the Portainer dashboard to       │
│    monitor container metrics and logs.   │
└─────────────────────────────────────────┘


┌─────────────────────────────────────────┐
│            Optimize Deployment           │
├─────────────────────────────────────────┤
│ 1. Review resource usage in the AWS     │
│    Management Console.                   │
│ 2. Scale your EC2 instance or adjust    │
│    Docker container resources as needed. │
└─────────────────────────────────────────┘

