# 🌩️ AWS Services - Training Handbook (2025)

---

## 📑 Table of Contents
1. [Introduction](#introduction)
2. [Cloud Computing Basics](#cloud-computing-basics)
   - What is Cloud Computing?
   - Why Cloud Instead of Traditional Data Centers?
   - Cloud Characteristics
   - Real-World Analogy: Electricity vs Cloud
3. [AWS Global Infrastructure](#aws-global-infrastructure)
   - Regions
   - Availability Zones (AZs)
   - Edge Locations
   - Local Zones
   - Wavelength Zones
   - Outposts
   - Example: How Netflix Uses AWS Global Infra
4. [AWS Account and Service Scope](#aws-account-and-service-scope)
   - AWS Account Structure
   - Service Scope (AZ, Regional, Global)
   - Identity and Access Management (IAM)
   - Example: Creating a New User
5. [Building an Application Architecture](#building-an-application-architecture)
   - Traditional Data Center (Before Cloud)
   - Three-Tier Architecture Explained
   - Scaling (Vertical vs Horizontal)
   - Load Balancing & DNS
   - Databases (Relational, NoSQL, Graph, Cache)
   - Storage (Internal vs External)
   - CDN (Content Delivery Network)
   - Analytics & Data Pipelines
   - Machine Learning & AI Features
   - Notifications, Messaging, Monitoring
   - Example: Designing a Social Media App
6. [AWS Core Services Explained](#aws-core-services-explained)
   - Compute: EC2, Lambda
   - Storage: S3, EBS
   - Databases: RDS, DynamoDB, Neptune, ElastiCache
   - Networking: VPC, Route53, ELB
   - Content Delivery: CloudFront
   - Analytics: Kinesis, Glue, EMR, Redshift, QuickSight
   - Machine Learning: SageMaker, AI APIs
   - Monitoring: CloudWatch
   - Messaging: SNS, SQS, SES
   - Example Mappings with Use Cases
7. [Infrastructure as Code (IaC)](#infrastructure-as-code-iac)
   - Why Manual Setup is Inefficient
   - AWS CloudFormation
   - Terraform
   - Example: Launching EC2 with CloudFormation
8. [DevOps on AWS](#devops-on-aws)
   - CI/CD Basics
   - AWS CodeCommit
   - AWS CodeBuild
   - AWS CodeDeploy
   - AWS CodePipeline
   - Example: Developer Push to Production Flow
9. [Learning Path and Certification](#learning-path-and-certification)
   - Foundational Services to Master
   - Role-Based Specializations
   - AWS Certifications Roadmap
   - Best Practices for Beginners
10. [Final Summary](#final-summary)

---

## 🌟 Introduction
Amazon Web Services (AWS) is the world’s leading cloud provider with **200+ services**.  
This handbook is designed for **absolute beginners** who want to understand AWS step by step.  
We’ll use **simple language, real-world analogies, and examples** so you can relate cloud concepts to everyday life.

---

## ☁️ Cloud Computing Basics

### 🔹 What is Cloud Computing?
Cloud computing means renting IT resources (like servers, storage, databases, or networking) over the internet instead of buying and managing them yourself.

**Key Features:**
- **On-Demand:** Use only when you need it.  
- **Pay-As-You-Go:** Pay for usage (like electricity bill).  
- **Scalable:** Grow or shrink resources as needed.  
- **Managed by Provider:** AWS handles hardware, networking, data centers.  

### 🔹 Why Cloud Instead of Traditional Data Centers?
**Traditional Data Centers:**
- You buy servers, maintain them, pay for electricity, hire staff.  
- Expensive and not flexible.  

**Cloud:**
- No upfront investment.  
- Quick setup (minutes instead of weeks).  
- Global reach.  

### 🔹 Real-World Analogy: Electricity vs Cloud
- Electricity → You don’t build a power plant at home. You pay for consumed units.  
- Cloud → You don’t buy servers. You pay AWS for the compute/storage you use.  

📌 **Example:** A startup launching a website can instantly use AWS servers instead of waiting months to buy & install hardware.

---

## 🌍 AWS Global Infrastructure

AWS builds **data centers worldwide** for high availability and low latency.

### 🔹 Regions
- Geographic areas like `us-east-1` (Virginia), `ap-south-1` (Mumbai).  
- As of 2025 → **34 regions**.  
- Customers choose the region closest to their users.  

### 🔹 Availability Zones (AZs)
- Each region has **3+ AZs**.  
- AZ = independent data center, 100km apart.  
- Ensures **fault tolerance**: if one AZ fails, another still serves.  

**Example:**  
Host your app in 2 AZs in Mumbai region. If AZ1 fails due to power outage, AZ2 keeps app online.

### 🔹 Edge Locations
- **600+ worldwide**.  
- Used for caching via **CloudFront CDN**.  
- Reduces latency for global users.  

**Example:**  
A user in India streams Netflix → Netflix caches videos at Mumbai edge → smooth streaming.

### 🔹 Local Zones
- AWS mini-data centers inside cities.  
- Ultra-low latency for local businesses.  

**Example:** Gaming companies in LA use AWS Local Zone in LA to serve players with 5ms latency.

### 🔹 Wavelength Zones
- AWS inside 5G telecom networks.  
- For apps needing **sub-10ms latency**.  

**Example:** Self-driving cars using real-time AWS services.

### 🔹 Outposts
- AWS racks installed **on-premises** at your office/data center.  
- For companies with data residency rules.  

**Example:** A bank that must keep data within its own country.  

---

## 🧾 AWS Account and Service Scope

### 🔹 AWS Account Structure
- **Top-level container** for all AWS resources.  
- Each account has:  
  - Billing  
  - Security (IAM)  
  - Services access  

### 🔹 Service Scope
- **AZ-scoped**: EC2 (runs in one AZ).  
- **Regional**: S3, DynamoDB.  
- **Global**: IAM, Route53, CloudFront.  

### 🔹 IAM (Identity and Access Management)
- Secure access to AWS.  
- Create **users, groups, roles, policies**.  

📌 **Example:**  
You don’t give root account to developers. Instead:  
- Create IAM user “Dev1”.  
- Assign permission (e.g., only S3 access).  

---

## 🏗️ Building an Application Architecture

Let’s design a **Social Media App** step by step.

### 🔹 Step 1: Three-Tier Architecture
1. **Web Tier** → Handles UI & requests.  
2. **App Tier** → Processes business logic.  
3. **Database Tier** → Stores data.  

### 🔹 Step 2: Scaling
- **Vertical Scaling:** Add RAM/CPU → limited.  
- **Horizontal Scaling:** Add more servers → recommended.  

### 🔹 Step 3: Load Balancer
- Distributes traffic among servers.  
- Ensures **high availability**.  

### 🔹 Step 4: DNS
- Maps domain (`myapp.com`) → Load Balancer IP.  

### 🔹 Step 5: Databases
- **Relational (RDS):** User accounts, orders.  
- **NoSQL (DynamoDB):** Posts, likes, comments.  
- **Graph (Neptune):** Friend relationships.  
- **Cache (ElastiCache):** Session data.  

### 🔹 Step 6: Storage
- **S3 for media files (images/videos).**  
- Metadata in DynamoDB.  

### 🔹 Step 7: CDN
- CloudFront caches images/videos near users.  

### 🔹 Step 8: Analytics
- Kinesis → collect clickstream data.  
- Glue → ETL.  
- Redshift → Data warehouse.  
- QuickSight → Dashboards.  

### 🔹 Step 9: Machine Learning
- SageMaker trains models → recommends friends.  
- Rekognition → filters inappropriate images.  

### 🔹 Step 10: Notifications
- SNS → Push notifications.  
- SES → Email.  
- SQS → Queue for chat messages.  

### 🔹 Step 11: Monitoring
- CloudWatch → monitors servers & apps.  

---

## 🔑 AWS Core Services Explained

### 🔹 Compute
- **EC2:** Virtual servers. Example → Run web app.  
- **Lambda:** Serverless. Example → Trigger function when image uploaded.  

### 🔹 Storage
- **S3:** Object storage, infinite capacity. Example → Store photos.  
- **EBS:** Block storage for EC2. Example → Attach disk to VM.  

### 🔹 Databases
- **RDS:** Managed SQL DB. Example → MySQL/Postgres.  
- **DynamoDB:** NoSQL, fast. Example → Likes on posts.  
- **Neptune:** Graph DB. Example → Friend connections.  
- **ElastiCache:** In-memory cache. Example → Store sessions.  

### 🔹 Networking
- **VPC:** Private network.  
- **ELB:** Load balancer.  
- **Route53:** DNS.  

### 🔹 Analytics
- **Kinesis:** Streaming data. Example → Clickstream.  
- **Glue:** ETL. Example → Clean data.  
- **EMR:** Big Data (Hadoop/Spark).  
- **Redshift:** Data warehouse.  
- **QuickSight:** BI dashboards.  

### 🔹 Machine Learning
- **SageMaker:** Build/train ML models.  
- **Rekognition:** Image analysis.  
- **Polly:** Text-to-speech.  
- **Translate:** Language translation.  

### 🔹 Monitoring
- **CloudWatch:** Logs, metrics, alerts.  

### 🔹 Messaging
- **SNS:** Notifications.  
- **SES:** Emails.  
- **SQS:** Message queues.  

---

## 🛠️ Infrastructure as Code (IaC)

### 🔹 Why Manual Setup is Inefficient?
- Hundreds of settings → prone to error.  
- Repetition needed across environments (Dev, Test, Prod).  

### 🔹 CloudFormation
- Templates in YAML/JSON.  
- Automates infra deployment.  

**Example:** Define VPC, EC2, RDS → CloudFormation builds it.

### 🔹 Terraform
- Multi-cloud tool.  
- Similar to CloudFormation but works beyond AWS.  

---

## 🔄 DevOps on AWS

### 🔹 CI/CD Flow
1. Developer pushes code → CodeCommit.  
2. CodeBuild compiles/tests code.  
3. CodeDeploy deploys to EC2/Lambda.  
4. CodePipeline automates the flow.  

📌 **Example:**  
- Developer commits `new_feature`.  
- Pipeline builds & tests.  
- If success → deployed to production.  

---

## 🎓 Learning Path and Certification

### 🔹 Step 1: Learn Core Services
- EC2, S3, RDS, DynamoDB, IAM, VPC.  

### 🔹 Step 2: Explore Advanced Areas
- Analytics, ML, DevOps.  

### 🔹 Step 3: Choose a Track
- Solutions Architect, DevOps Engineer, Data Engineer, ML Engineer.  

### 🔹 Step 4: Certifications
1. **AWS Certified Cloud Practitioner** (beginner).  
2. **AWS Solutions Architect Associate**.  
3. Advanced Role-specific Certifications.  

### 🔹 Best Practices for Beginners
- Hands-on practice on free tier.  
- Start with one project (e.g., host a website).  
- Learn IAM thoroughly (security first).  

---

## ✅ Final Summary
- AWS provides **on-demand cloud services** like compute, storage, DBs, and networking.  
- Global infra ensures **low latency** worldwide.  
- Applications use **scalable architecture** with load balancing, caching, and CDN.  
- AWS has **purpose-built databases** and **analytics tools**.  
- **Infrastructure as Code** (CloudFormation/Terraform) automates deployments.  
- DevOps pipelines streamline delivery.  
- Beginners should start with **core services + certification** to build strong foundation.  

---
