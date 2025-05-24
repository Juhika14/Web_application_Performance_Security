# Web_application_Performance_Security
# 🌐 Scalable and Secure Web Application on AWS

This project demonstrates the architecture and deployment of a **highly available, scalable, and secure web application** on AWS using:

- **Amazon API Gateway** (HTTP Proxy Integration)
- **AWS Global Accelerator** (for global performance)
- **Amazon CloudFront** (for content delivery and caching)

## 📌 Architecture Overview

              +------------------+
              |   End Users      |
              +--------+---------+
                       |
                       v
           +--------------------------+
           |   AWS Global Accelerator |
           +--------------------------+
                /               \
               /                 \
      +----------------+   +------------------+
      | EC2 (Virginia) |   |   ALB (Oregon)    |
      |  Web Server    |   |  → EC2 WebServer  |
      +----------------+   +------------------+
               \               /
                \             /
                 v           v
              +--------------------+
              |  Amazon CloudFront |
              +--------------------+
                       |
                       v
              +-------------------+
              | Amazon API Gateway|
              | (HTTP Proxy)      |
              +-------------------+

---

## 🚀 Features

- ✅ REST API built with **Amazon API Gateway**
- 🌍 Low-latency global access via **AWS Global Accelerator**
- ⚡ High-speed content delivery with **Amazon CloudFront**
- 🌐 Redundant deployment in **two regions**: N. Virginia and Oregon
- 🔒 Secure traffic routing using **HTTPS** and best practices

---

## 🛠️ Setup Instructions

### Step 1: Launch EC2 Web Server (N. Virginia)

1. Launch EC2 in **us-east-1**
2. Use the following **User Data**:
   ```bash
   #!/bin/bash
   yum update -y
   yum install httpd -y
   systemctl start httpd
   systemctl enable httpd
   echo "<h1>Web Server - N. Virginia</h1>" > /var/www/html/index.html
