# 🚀 Portainer Deployment on AWS EC2

![Portainer Logo](https://www.portainer.io/images/portainer-logo.svg)

## Overview
This project showcases the successful deployment of **Portainer**, a powerful management UI for Docker, on an **Amazon EC2** instance. The aim is to streamline container orchestration and management, providing a user-friendly interface for managing Docker containers and images.

---

<div align="center">
    <svg width="100%" height="30">
        <rect width="100%" height="100%" fill="#4CAF50"/>
    </svg>
</div>

## Key Responsibilities

### 🛠 Infrastructure Setup
- Launched an EC2 instance with optimal configurations for container deployment.

<div align="center">
    <svg width="100%" height="30">
        <rect width="100%" height="100%" fill="#2196F3"/>
    </svg>
</div>

### 🚀 Portainer Installation
- Utilized **Docker Compose** to deploy Portainer, enabling a user-friendly interface for managing Docker containers and images.

<div align="center">
    <svg width="100%" height="30">
        <rect width="100%" height="100%" fill="#FFC107"/>
    </svg>
</div>

### 🔐 Security Configuration
- Implemented AWS security group rules to ensure secure access to the Portainer interface while adhering to best practices for network security.

<div align="center">
    <svg width="100%" height="30">
        <rect width="100%" height="100%" fill="#FF5722"/>
    </svg>
</div>

### 👥 User Management
- Configured role-based access control in Portainer, allowing for secure multi-user access and management of containerized applications.

<div align="center">
    <svg width="100%" height="30">
        <rect width="100%" height="100%" fill="#9C27B0"/>
    </svg>
</div>

### 📊 Monitoring and Optimization
- Monitored performance metrics and optimized the deployment for improved reliability and efficiency.

---

## Getting Started

### Prerequisites
- An **AWS account**
- Basic knowledge of **Docker** and **AWS EC2**

### Installation Steps

1. **Launch EC2 Instance**
   - Go to the AWS Management Console and launch a new EC2 instance.
   - Choose an Amazon Machine Image (AMI) suitable for your needs.
   - Configure instance type, security group, and key pair.

2. **Connect to Your EC2 Instance**
   - Connect to your EC2 instance via SSH:
     ```bash
     ssh -i "your-key.pem" ec2-user@<your-ec2-instance-public-ip>
     ```

3. **Install Docker**
   - Update the package database:
     ```bash
     sudo yum update -y
     ```
   - Install Docker:
     ```bash
     sudo amazon-linux-extras install docker
     ```
   - Start the Docker service:
     ```bash
     sudo service docker start
     ```
   - Add the `ec2-user` to the `docker` group to run Docker commands without `sudo`:
     ```bash
     sudo usermod -aG docker ec2-user
     ```
   - Log out and log back in to refresh your group membership:
     ```bash
     exit
     ```

4. **Install Docker Compose**
   - Run the following command to install Docker Compose:
     ```bash
     sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
     sudo chmod +x /usr/local/bin/docker-compose
     ```

5. **Deploy Portainer**
   - Create a `docker-compose.yml` file with the following content:
     ```yaml
     version: '3.3'
     services:
       portainer:
         image: portainer/portainer-ce
         ports:
           - "9000:9000"
         volumes:
           - /var/run/docker.sock:/var/run/docker.sock
           - portainer_data:/data
     volumes:
       portainer_data:
     ```
   - Run the following command to deploy Portainer:
     ```bash
     docker-compose up -d
     ```

6. **Access Portainer**
   - Open your web browser and navigate to `http://<your-ec2-instance-public-ip>:9000`.
   - Follow the setup instructions to create an admin account.

---

## Contributing
Feel free to submit issues or pull requests for any improvements or suggestions.

## License
This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- [Portainer](https://www.portainer.io/) for providing a great tool for Docker management.
- [AWS](https://aws.amazon.com/) for their cloud services.

---

## Contact
For any inquiries, please reach out to me at [mohammedrashwan.com](https://mohammedrashwan.com).
