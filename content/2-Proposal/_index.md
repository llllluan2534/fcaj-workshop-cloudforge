---
title: "Proposal"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Smart Media Analytics
## Building an AI-powered Video Analysis (Semantic Search System)

### 1. Executive Summary
Smart Media Analytics (SMA) is a local-first media management and search system designed for video editors, designers, and research teams needing rapid retrieval of media content. The system automates media ingestion, scene splitting, transcription, and AI-powered contextual description, enabling natural language search.
Initially, SMA runs entirely on local machines (via Docker) to ensure privacy and cut experimental costs. For production scaling, it offers a seamless upgrade path to AWS (S3, Bedrock, OpenSearch, RDS).

### 2. Problem Statement
**Current Problem:** Managing media is tedious due to scattered data and manual searching for specific scenes or dialogues. Relying directly on cloud AI services for the entire pipeline incurs high costs and potential data privacy risks.
**Solution:** SMA addresses this with an automated pipeline utilizing a React dashboard, FastAPI, ChromaDB, PostgreSQL, MinIO, and local AI models (Ollama, faster-whisper). Users simply type "beach sunset" to jump exactly to the desired video timestamp. This significantly reduces manual effort and optimizes infrastructure costs.

### 3. Solution Architecture
SMA is designed with a hybrid local-to-cloud approach to be convenient for internal development while remaining easy to upgrade to a production environment later. In the local phase, the entire media ingest workflow runs in Docker Compose: the system receives videos and images, automatically detects scenes, transcribes audio, generates AI content descriptions, and saves processed data locally.

When deploying to AWS, the architecture can scale without major changes to the processing logic. S3 is used for media storage, Bedrock and Transcribe handle the AI components, RDS PostgreSQL stores metadata, CloudFront combined with S3 delivers the frontend interface, while services like Cognito, WAF, ECR, Lambda, ECS Fargate, App Runner, Step Functions, SQS, EventBridge, CloudWatch, X-Ray, ElastiCache, and VPC support security, orchestration, monitoring, and system scaling.

![SMA Architecture](/images/2-Proposal/1.SMA_architecture.png)
![SMA Architecture](/images/2-Proposal/2.SMA_architecture.png)

**AWS Services Integrated in the Architecture:**
- **Networking & Delivery:**
  - **Amazon Route 53**: DNS management.
  - **Amazon CloudFront**: CDN for rapid delivery of the React frontend and media.
  - **Amazon VPC**: Secure virtual network, utilizing a **NAT Gateway** and Internet Gateway for private subnet outbound access.
- **Security & Identity:**
  - **AWS WAF**: Web Application Firewall to protect against common exploits.
  - **Amazon Cognito**: User authentication and authorization (JWT tokens).
  - **AWS Secrets Manager**: Secure storage for DB credentials and API keys.
- **Storage & Databases:**
  - **Amazon S3**: Object storage for original media and keyframes (with **S3 Gateway Endpoint**).
  - **Amazon RDS (PostgreSQL)**: Primary relational database for metadata (Multi-AZ).
  - **Amazon ElastiCache (Redis)**: High-speed in-memory cache for queries.
- **Compute & API:**
  - **AWS App Runner**: Simplified, auto-scaling deployment for the FastAPI backend.
  - **Amazon API Gateway**: Routing for REST APIs and WebSocket (WSS Push).
  - **Amazon ECS (AWS Fargate)**: Serverless compute for video processing Auto Scaling tasks.
  - **AWS Lambda**: Event-driven serverless code execution (e.g., saving embeddings).
- **Artificial Intelligence (AI/ML):**
  - **Amazon Bedrock**: Utilizes models like Nova Lite & Titan Embeddings for semantic analysis and vector generation.
  - **Amazon Transcribe**: Automated Speech-to-Text for audio extraction.
- **Integration & Orchestration:**
  - **Amazon SQS & Amazon EventBridge**: Message queues and event bus for decoupled communication.
  - **AWS Step Functions**: Workflow orchestration for the complex video processing pipeline.
- **DevOps & Monitoring:**
  - **Amazon ECR**: Secure registry for Docker images.
  - **Amazon CloudWatch & AWS X-Ray**: Comprehensive logging, metric alarms, and Distributed Tracing.

**Core Component Design**
- **Frontend Layer**: React app stored on S3, distributed by CloudFront + Route 53, protected by WAF and Cognito.
- **API & Routing Layer**: API Gateway routes traffic to the FastAPI service hosted on App Runner.
- **Processing & AI Layer**: Step Functions coordinates EventBridge and SQS to trigger ECS (Fargate) tasks for scene detection, followed by Bedrock & Transcribe for AI extraction.
- **Data Layer**: Metadata is persisted in RDS PostgreSQL, cached in ElastiCache. Lambda handles writing vectors and saving media objects to S3. The entire data layer is secured within a VPC with a NAT Gateway.

### 4. Implementation Phases
The project is divided into 4 main phases:
1. **Architectural Research**: Map the data flow to the extensive AWS services list.
2. **Local-first Build**: Develop and refine the core logic locally using Docker.
3. **AWS Cloud-ready Integration**: Incrementally replace local containers with AWS managed services (e.g., App Runner, Bedrock, S3).
4. **CI/CD & Monitoring**: Push images to ECR via GitHub Actions, set up CloudWatch alarms, and enable X-Ray tracing.

### 5. Budget Estimation (AWS Environment)
Deploying this comprehensive production architecture with over 20 AWS services (including Multi-AZ and a 24/7 NAT Gateway), the budget for a small-scale or lab environment is estimated as follows:

| AWS Service | Use Case | Estimated Cost/Month (USD) |
| --- | --- | --- |
| **Amazon RDS (PostgreSQL)** | Primary Database (Multi-AZ, `db.t4g.medium`, 20GB) | $68.00 |
| **AWS NAT Gateway** | Allows Private Subnet internet access (1 NAT, 24/7) | $32.40 |
| **Amazon ElastiCache** | Cache (Multi-AZ, `cache.t4g.micro`, 2 nodes) | $32.00 |
| **Amazon ECS (Fargate)** | Auto Scaling Task for Video Processing (~1 vCPU, 2GB RAM) | $15.00 |
| **Amazon Bedrock & Transcribe** | AI, Speech-to-Text, Embeddings (Base estimate) | $15.00 |
| **AWS App Runner** | Web Service / API (Minimum 1 instance) | $7.00 |
| **AWS WAF** | Web Application Firewall (1 Web ACL, 1 Rule) | $6.00 |
| **Amazon CloudWatch & X-Ray** | Logs, Metrics, Alarms, Distributed Tracing | $5.00 |
| **Amazon S3** | Media & Keyframe Storage (Est. ~50GB) | $2.00 |
| **AWS Secrets Manager** | Keys & Credentials Management (5 secrets) | $2.00 |
| **Amazon API Gateway** | REST API & WSS Push (Request-based) | $1.00 |
| **Amazon CloudFront** | Content Delivery CDN (Data Transfer) | $1.00 |
| **Amazon SQS, EventBridge, Step Functions** | Workflow Orchestration, Event Bus, Queues | $1.00 |
| **Amazon Route 53** | DNS Management (1 Hosted Zone) | $0.50 |
| **Amazon Cognito** | User Authentication (JWT) | $0.00 (Free Tier) |
| **AWS Lambda** | Metadata & Embedding Storage | $0.00 (Free Tier) |
| **Estimated Total** | **Entire System** | **~$187.90** |

### 6. Risk Assessment & Expected Outcomes
- **Risk Matrix:** Cloud scaling costs could increase, and local AI inference may be slow.
- **Mitigation Strategies:** Limit batch ingests, cache results aggressively, and only migrate necessary components to cloud services (like Bedrock/OpenSearch) when required.
- **Expected Outcomes:** A highly efficient Media Intelligence system that empowers creative teams to search media via natural language, complete with a flexible infrastructure roadmap.