# ☁️ Cloud-Hosted Resume Website

This repository contains the code and infrastructure for my personal resume website, fully deployed and automated on AWS. The project demonstrates modern cloud engineering, serverless backend design, and Infrastructure as Code practices.


🚀 Features

Static Resume Website

Hosted on Amazon S3, served securely via CloudFront, with a custom domain managed by Route 53.

Visitor Counter API

Backend: AWS Lambda + API Gateway

Database: DynamoDB for persistent visitor tracking

Functionality written in Python

CI/CD Automation

GitHub Actions for automated builds and deployments

Terraform for Infrastructure as Code (IaC), ensuring consistency and scalability

Security & Performance

HTTPS with AWS Certificate Manager (ACM)

Global distribution with CloudFront caching

```mermaid
flowchart TB;
  A[User (Browser)];
  B[Route 53];
  C[CloudFront];
  D[S3];
  A --> B --> C --> D;
'''
