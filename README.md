# 🚀 NginxVerse – Nginx Server Deployment Using Docker on AWS EC2

A modern, responsive website deployed using **Docker containerization** on an **AWS EC2 instance**, powered by the Nginx web server.

This project demonstrates how to build a custom Docker image, run an Nginx container, configure port mapping, and make a website accessible over the internet using AWS infrastructure.

<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws" />
  <img src="https://img.shields.io/badge/Docker-Containerization-blue?logo=docker" />
  <img src="https://img.shields.io/badge/Nginx-Web%20Server-green?logo=nginx" />
  <img src="https://img.shields.io/badge/Status-Completed-success" />
</p>

---

## 🌐 Live Project

**Visit the deployed website:**

[🚀 View NginxVerse – Live Website](http://13.60.213.23:8080)

---

## 📌 Project Overview

The objective of this project is to deploy a custom-designed website using Docker on an AWS EC2 virtual machine.

Instead of installing and configuring Nginx directly on the host operating system, Docker is used to package the website with the Nginx web server into a containerized environment.

The website is served through Nginx and accessed using the public IPv4 address of the EC2 instance.

## 🏗️ Architecture

```text
              AWS CLOUD
                  |
             AWS EC2
                  |
             Docker Engine
                  |
              Dockerfile
                  |
             Docker Image
            nginx-custom:v1
                  |
            Docker Container
                nginx-web
                  |
          Port Mapping 8080:80
                  |
            Nginx Web Server
                  |
             Custom Website
               NginxVerse
                  |
          Browser / Internet
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Cloud virtual machine |
| Amazon Linux 2023 | Operating system |
| Docker | Containerization platform |
| Nginx | Web server |
| HTML5 | Website structure |
| CSS3 | Website styling and responsive design |
| Linux | Server administration |

## ⚙️ Implementation Steps

### 1. Launch AWS EC2 Instance

- Launched an EC2 virtual machine using Amazon Linux 2023.
- Selected the `t3.micro` instance type.
- Configured the instance and storage.
- Connected to the instance.

### 2. Update Linux Packages

```bash
sudo su
yum update -y
```

Updated the Linux packages before installing Docker.

### 3. Install Docker

```bash
yum install docker -y
```

Start Docker:

```bash
systemctl start docker
```

Enable Docker at system startup:

```bash
systemctl enable docker
```

Verify Docker:

```bash
docker --version
```

### 4. Create Project Directory

```bash
mkdir nginx-docker-project
cd nginx-docker-project
```

### 5. Create Custom Website

Created an `index.html` file containing a responsive NginxVerse landing page using HTML, CSS, and visual effects.

### 6. Create Dockerfile

Created a Dockerfile to package the custom website with the official Nginx image.

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

**Dockerfile explanation:**

- `FROM`: Uses the official Nginx image as the base image.
- `COPY`: Copies the custom website into the Nginx web directory.
- `EXPOSE`: Documents the container port used by Nginx.

### 7. Build Custom Docker Image

```bash
docker build -t nginx-custom:v1 .
```

Created a custom Docker image named `nginx-custom` with version tag `v1`.

Verify the image:

```bash
docker images
```

### 8. Run Docker Container

```bash
docker run -d --name nginx-web -p 8080:80 nginx-custom:v1
```

**Command explanation:**

- `-d`: Runs the container in detached mode.
- `--name`: Assigns the container name.
- `-p 8080:80`: Maps host port 8080 to container port 80.
- `nginx-custom:v1`: Specifies the Docker image.

### 9. Verify Running Container

```bash
docker ps
```

Verified that the Nginx container was running with the required port mapping.

### 10. Configure AWS Security Group

Configured an inbound security group rule:

| Setting | Configuration |
|---|---|
| Type | Custom TCP |
| Protocol | TCP |
| Port | 8080 |
| Source | My IP |

This allowed authorized external access to the website.

### 11. Access the Website

Opened the website using the EC2 public IPv4 address:

```text
http://YOUR-EC2-PUBLIC-IP:8080
```

Successfully accessed the custom NginxVerse website through the browser.

---

## 📂 Project Structure

```text
nginx-docker-project/
│
├── Dockerfile
│
└── index.html
```

## 🔍 Verification Commands

Check Docker version:

```bash
docker --version
```

List Docker images:

```bash
docker images
```

Check running containers:

```bash
docker ps
```

Check container logs:

```bash
docker logs nginx-web
```

Test the Nginx server:

```bash
curl -I http://localhost:8080
```

## 📸 Project Screenshots

Project implementation screenshots and documentation are available in this repository.

- EC2 Instance Configuration
- Docker Installation
- Custom HTML Website
- Dockerfile Configuration
- Docker Image Build
- Running Docker Container
- AWS Security Group
- Final Website Deployment

## 📄 Project Documentation

For the complete implementation guide, architecture, commands, explanations, and screenshots, refer to:

**[📘 Nginx Docker Deployment – Project Documentation (PDF)](Nginx-Docker-Deployment-AWS-EC2.pdf)**

## 🎯 Key Learnings

Through this hands-on project, I gained practical experience in:

- Launching and managing AWS EC2 instances.
- Performing Linux server administration.
- Installing and managing Docker.
- Creating custom Docker images using Dockerfiles.
- Running and managing Docker containers.
- Understanding Docker port mapping.
- Deploying Nginx using containerization.
- Configuring AWS Security Groups.
- Hosting and accessing a custom website through a public IP address.

## 🔮 Future Improvements

- Push the custom Docker image to Docker Hub.
- Automate deployment using Jenkins CI/CD.
- Configure HTTPS using SSL/TLS.
- Add a custom domain name.
- Explore container orchestration using Kubernetes.

---

## 👨‍💻 Author

**Bashir Shaikh**

Aspiring Cloud & DevOps Engineer

Interested in AWS, Docker, Linux, Cloud Infrastructure, and DevOps automation.

---

⭐ If you find this project useful, feel free to explore the repository and connect with me!
