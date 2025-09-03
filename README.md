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

flowchart TB
  %% =========================
  %% Cloud Resume Architecture
  %% =========================
  %% Client
  U[User (Browser)]

  %% DNS / Edge / Storage
  R53[Route 53<br/>DNS: uchennaokoronkwo.com & www]
  CF[CloudFront<br/>Distribution]
  ACM[ACM Certificate (us-east-1)<br/>for apex + www]
  S3[S3 Bucket<br/>(Static site content)]

  %% API / Counter
  APIGW[API Gateway<br/>/count endpoint]
  LAMBDA[Lambda<br/>Visitor counter function]
  DDB[DynamoDB<br/>VisitorCount table]
  IAM[IAM Role<br/>(Lambda execution)]

  %% CI/CD & IaC
  subgraph CICD[CI/CD & IaC]
    GH[GitHub Actions<br/>build/test/deploy]
    TF[Terraform<br/>provisioning]
  end

  %% -------------------------
  %% User → DNS → Edge → S3
  %% -------------------------
  U -->|DNS query| R53 -->|ALIAS A/AAAA| CF
  U -->|HTTPS| CF -->|Origin request| S3
  ACM -.->|TLS cert| CF

  %% -------------------------
  %% Visitor Counter Path
  %% -------------------------
  %% (Either route /api/* through CloudFront or call API Gateway directly)
  CF -- optional behavior for /api/* --> APIGW
  U ---->|HTTPS (direct call)| APIGW
  APIGW --> LAMBDA --> DDB
  IAM -.->|permissions| LAMBDA

  %% -------------------------
  %% CI/CD & IaC flows
  %% -------------------------
  GH -->|Upload site assets| S3
  GH -->|Invalidate cache| CF

  TF -.->|Create/Update| R53
  TF -.->|Create/Update| CF
  TF -.->|Request/validate| ACM
  TF -.->|Create/Update| S3
  TF -.->|Create/Update| APIGW
  TF -.->|Create/Update| LAMBDA
  TF -.->|Create/Update| DDB

