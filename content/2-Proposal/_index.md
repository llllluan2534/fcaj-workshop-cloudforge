---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# Smart Media Analytics
## Internal AI Solution for Semantic Media Management, Search, and Analysis

### 1. Executive Summary
Smart Media Analytics (SMA) is a local-first media management and search system designed for video editors, designers, and research teams who need to quickly search for image, video, and audio content. The system allows media ingestion, automatic scene splitting, content transcription, AI-powered contextual description, and natural language search. This helps users quickly find the exact asset or timestamp in a video without manually reviewing the entire file.

In the internal development phase, SMA prioritizes running entirely on local machines via Docker to ensure data privacy and reduce experimental costs. When scaling to a production environment, the system can be migrated to AWS using a corresponding architecture that includes S3, Bedrock, Transcribe, OpenSearch Serverless, RDS PostgreSQL, CloudFront, Cognito, and WAF. This approach makes SMA suitable for the prototype phase while providing a clear path for long-term scalability.

### 2. Problem Statement
**Current Problem**
Managing media is often difficult because data is scattered across multiple locations, file names do not reflect content, and finding the exact scene or dialogue in a video must be done manually. For creative or research projects, this consumes a lot of time, especially as media libraries grow over time. Furthermore, using cloud AI services directly for the entire pipeline can lead to rapidly increasing costs and the risk of internal data leaks.

**Solution**
SMA solves this problem with an automated, local-first media processing pipeline. The system uses a React dashboard to browse assets, FastAPI to provide APIs, ChromaDB to store and query vector embeddings, PostgreSQL to store metadata, MinIO for media object storage, Ollama to run vision and embedding models locally, and faster-whisper for audio transcription.
When deployed on AWS, these components are mapped to their corresponding production architecture: MinIO to Amazon S3, the Ollama vision model to AWS Bedrock, faster-whisper to Amazon Transcribe, ChromaDB to Amazon OpenSearch Serverless, and PostgreSQL to Amazon RDS PostgreSQL. Additionally, the cloud system can utilize CloudFront, Cognito, WAF, ECR, CloudWatch, Secrets Manager, and CI/CD via GitHub Actions to complete the deployment lifecycle.

**Benefits and Return on Investment (ROI)**
The solution significantly shortens the time required to find footage, read transcripts, and identify needed scenes, thereby increasing productivity for creative teams. Users can enter natural queries like "sunset on the beach with sound of waves" and get the exact video clip and timestamp, rather than manually watching the entire file.
In the long term, SMA can serve as an internal media intelligence platform for labs or small businesses. ROI comes from saving time on manual processing, reducing media search costs, and avoiding expensive commercial media management tools.

### 3. Solution Architecture
SMA is built on a hybrid local-to-cloud model. At the local layer, the entire ingest pipeline runs in Docker Compose: videos and images are fed into the system, scenes are split using PySceneDetect, audio is transcribed with faster-whisper, image content is described using a vision model via Ollama, and the data is vector-embedded and stored in ChromaDB.
At the cloud layer, the architecture can be upgraded to AWS production without rewriting the entire system. S3 acts as media storage, Bedrock handles multimodal AI, Transcribe creates transcripts, OpenSearch Serverless manages semantic search, and RDS PostgreSQL stores metadata. CloudFront + S3 can be used to distribute the frontend UI. Cognito, WAF, Secrets Manager, ECR, and CloudWatch support security, container registries, monitoring, and operations.

![SMA Architecture](/images/2-Proposal/SMA_architecture.png)

**AWS Services Used**
- **Amazon S3**: Stores original media, thumbnails, scene frames, and intermediate data.
- **AWS Bedrock**: Supports multimodal AI models for describing image/video content and generating semantic search embeddings.
- **Amazon Transcribe**: Converts speech in videos to text for transcript-based search.
- **Amazon OpenSearch Serverless**: Stores vector embeddings and serves semantic searches.
- **Amazon RDS PostgreSQL**: Stores metadata for assets, scenes, transcripts, tags, and ingest status.
- **Amazon CloudFront**: Delivers the frontend quickly and reliably.
- **Amazon Cognito**: Authenticates and authorizes user access to the dashboard.
- **AWS WAF**: Protects the web layer from common exploits and unauthorized access.
- **Amazon ECR**: Stores Docker images for CI/CD processes.
- **AWS CloudWatch**: Logs, monitors, and alerts on system status.
- **AWS Secrets Manager**: Stores sensitive configurations, tokens, and secrets.
- **GitHub Actions**: Automates building and pushing images in the deployment pipeline.

**Component Design**
- **Frontend**: React 19 + Vite + Tailwind CSS, providing a dashboard for searching, previewing, and managing assets.
- **Backend API**: FastAPI handles ingest, search, asset details, and business APIs.
- **Ingest Pipeline**: Scene splitting, caption generation, transcription, embedding generation, and metadata storage.
- **Vector Search**: ChromaDB locally or OpenSearch Serverless on AWS.
- **Object Storage**: MinIO locally or S3 on AWS.
- **Database**: PostgreSQL locally or RDS PostgreSQL on AWS.
- **Security & Ops**: Cognito, WAF, Secrets Manager, CloudWatch, and CI/CD via GitHub Actions.

### 4. Technical Implementation
**Implementation Phases**
The SMA project can be divided into 4 main phases:
1. **Research and Architectural Design**: Analyze media search requirements, timestamp seeking, ingest pipelines, and map them to AWS targets.
2. **Build Local-First Version**: Finalize Docker Compose, FastAPI, React dashboard, ChromaDB, PostgreSQL, MinIO, and internal AI modules.
3. **Standardize for Cloud-Ready**: Separate configurations to easily replace local components with corresponding AWS services.
4. **Deployment and Testing**: Set up CI/CD, container registry, security, monitoring, and test the cloud deployment.

**Technical Requirements**
- **Frontend**: React 19, Vite, Tailwind CSS, featuring a video player with timestamp seeking.
- **Backend**: Python 3.11, FastAPI, Uvicorn.
- **AI Pipeline**: Ollama running vision and embedding models, faster-whisper for ASR, PySceneDetect and FFmpeg for video processing.
- **Data Layer**: PostgreSQL 16, ChromaDB, MinIO locally; mapping to RDS, OpenSearch Serverless, and S3 on AWS.
- **Deployment**: Docker Compose for local environments, GitHub Actions for CI/CD, ECR for container registries, and CloudFront + S3 for frontend production.

### 5. Summary of AWS Deployment
Once the local-first version is complete, the SMA system can be migrated to AWS step-by-step to minimize risk while maintaining core processing logic. In the storage layer, MinIO will be replaced by Amazon S3 to store original media, thumbnails, and intermediate files. In the AI and semantic processing layer, the Ollama vision model can be replaced by AWS Bedrock, faster-whisper by Amazon Transcribe, and ChromaDB transitioned to Amazon OpenSearch Serverless for large-scale semantic search.

Structured data will be moved to Amazon RDS PostgreSQL to ensure better durability and manageability compared to running locally. The React interface can be built and distributed via Amazon S3 combined with CloudFront to accelerate access, while Amazon Cognito authenticates users and AWS WAF secures the web layer. For automated deployment, GitHub Actions can be used to build Docker images, push them to Amazon ECR, and deploy the backend to the AWS environment.

This deployment approach allows SMA to maintain its local-first model during development but provides a clear roadmap for scaling to production on AWS as media volume, users, and queries grow.

### 6. Introduction to AWS Services Used
During the cloud deployment phase, SMA leverages managed services to reduce operational effort and improve scalability. Amazon S3 is used for storing raw media, thumbnails, and intermediate files. AWS Bedrock handles AI tasks like describing image/video content, while Amazon Transcribe converts audio to text for dialogue-based search. Amazon OpenSearch Serverless is utilized for semantic search and vector retrieval, and Amazon RDS PostgreSQL stores metadata for assets, scenes, transcripts, and tags.
Additionally, Amazon CloudFront and S3 can distribute the frontend, Amazon Cognito secures user logins, AWS WAF enhances web layer security, Amazon ECR stores Docker images, and CloudWatch alongside Secrets Manager support monitoring and sensitive configuration management. By clearly separating these roles, the system is suitable for internal environments and offers a clear upgrade path to production.

### 7. Budget Estimation
In the local-first phase, costs are virtually $0/month as all processing runs on personal or lab machines. When deployed on AWS, costs will depend on media volume, video duration, ingest frequency, and user search volume.
For a small scale in a lab or a small team, a rough estimate is as follows:
- **Amazon S3**: ~$0.5 - $1.5/month for a few GBs of media and thumbnails.
- **Amazon RDS PostgreSQL**: ~$15 - $25/month for a small metadata instance.
- **Amazon OpenSearch Serverless**: ~$5 - $20/month, as AWS charges based on OCUs for ingest and search, alongside S3 storage.
- **Amazon Transcribe**: ~$1 - $5/month for processing a small amount of audio.
- **AWS Bedrock**: ~$2 - $10/month depending on the number of image/video descriptions and embedding generations.
- **CloudFront, Cognito, WAF, ECR, CloudWatch**: ~$1 - $5/month for basic usage.

**Total Estimate**: ~$24 - $66/month for a small scenario. This could be lower for purely internal testing or higher if media volume and search queries increase significantly. For more precise figures, the AWS Pricing Calculator should be used once data volume and expected loads are finalized.

### 8. Risk Assessment
**Risk Matrix**
- Large media volume: High impact, medium probability.
- Slow local AI model execution: Medium impact, high probability.
- Search result inaccuracies: Medium impact, medium probability.
- Increased cloud costs when scaling: High impact, low to medium probability.

**Mitigation Strategies**
- Use a step-by-step local pipeline, cache models, and optimize batch processing.
- Strictly separate metadata, vector search, and object storage for easy AWS substitution.
- Limit ingest batches and monitor performance via logs/metrics.
- Only migrate components that need scaling to the cloud rather than moving everything initially.

**Contingency Plans**
- If local AI inference is too heavy, reduce model size or migrate to Bedrock early during the cloud phase.
- If local vector search is slow, migrate to OpenSearch Serverless sooner.
- If the ingest pipeline fails, the system retains basic metadata to avoid losing the entire media library.

### 9. Expected Outcomes
- **Technical**: SMA allows users to ingest media, automatically create semantic indexes, search via natural language, and jump directly to the exact timestamp in a video.
- **Product**: The system is ideal for design teams, video editors, content researchers, or labs needing secure and efficient internal media management.
- **Scalability**: The local-first architecture enables rapid development, while AWS mapping gives the system a clear upgrade path to a production environment when needed.