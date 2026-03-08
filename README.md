# Cloud-Hosted Resume Project

This repository contains a **cloud-hosted resume website** deployed on **AWS** with Infrastructure as Code (IaC) and CI/CD automation.  
It demonstrates practical skills in **AWS services**, **Terraform**, **CI/CD pipelines**, and **serverless application design**.

---

## Architecture

<img width="1622" height="822" alt="image" src="https://github.com/user-attachments/assets/78d1626e-6245-4734-b95d-c2e2427ecfd3" />


### Legend
- **Route 53** → DNS for `uchennaokoronkwo.com`  
- **AWS Certificate Manager (ACM)** → SSL/TLS certificate for HTTPS  
- **CloudFront** → CDN for caching + distribution  
- **S3** → Static website hosting (HTML/CSS)  
- **API Gateway** → HTTP API entry point  
- **Lambda** → Serverless function for visitor counter  
- **DynamoDB** → NoSQL DB storing visitor count  
- **GitHub / Actions** → CI/CD pipeline for automated deployments  
- **Terraform** → Infrastructure as Code (manages backend resources)

> **Note:** Backend resources (API Gateway, Lambda, DynamoDB, IAM) are fully managed by Terraform.  
> Frontend resources (Route 53, CloudFront, S3, ACM) are manually deployed but integrated into CI/CD for updates.

---

## Features
- Custom domain with HTTPS (via Route 53 + ACM)  
- Static resume website hosted in **Amazon S3**  
- Global distribution and caching via **CloudFront**  
- Visitor counter implemented with **API Gateway → Lambda → DynamoDB**  
- Automated deployments with **GitHub Actions**  
- Backend Infrastructure as Code using **Terraform**  

---

## Technologies Used
- **AWS**: Route 53, ACM, CloudFront, S3, API Gateway, Lambda, DynamoDB, IAM  
- **Terraform**: Infrastructure provisioning for backend services  
- **GitHub Actions**: CI/CD for deployments  
- **Python**: Lambda function logic  
- **HTML/CSS**: Frontend static resume site  

---

## Deployment Workflow
1. Developer pushes changes to GitHub.  
2. GitHub Actions pipeline runs:  
   - Builds and syncs static website files to S3.  
   - Invalidates CloudFront cache.  
   - Runs Terraform to provision/update backend infrastructure.  
3. End users access the site via `uchennaokoronkwo.com`, served securely and globally.  

---

## Visitor Counter Example
The site includes a live visitor counter powered by DynamoDB.  
Each page load invokes API Gateway → Lambda → DynamoDB, which automatically increments and returns the visitor count.

---

## Resume
You can view my live cloud-hosted resume here:  
[https://uchennaokoronkwo.com](https://uchennaokoronkwo.com)
