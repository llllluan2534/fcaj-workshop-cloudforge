---
title: "Blog 1"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Building Your First Search Application with Amazon OpenSearch Service

In today's data-driven world, the ability to search and analyze information in real time is no longer a competitive advantageâ€”it is a business necessity. From industrial IoT sensors streaming millions of metrics per second, to e-commerce platforms that must instantly surface relevant products, and security teams that need to detect threats as they emerge, all require a powerful search and analytics platform.

This is where Amazon OpenSearch Service comes in.

## What is OpenSearch Service?

Amazon OpenSearch Service is a fully managed search and analytics service provided by AWS. Instead of worrying about infrastructure management, developers can focus on building applications and delivering business value.

The Amazon OpenSearch Serverless offering goes even further by automatically scaling resources based on demand, eliminating the need to manage servers altogether.

## Core Concepts You Should Know

Before diving into implementation, it's important to understand several foundational concepts:

### Document & Index

The basic unit of data in OpenSearch is a document, typically stored in JSON format. Documents are organized into indices, which are similar to tables in a traditional database.

### Cluster & Node

OpenSearch operates on a distributed architecture.

Master nodes manage cluster operations and metadata.
Data nodes store data and execute search queries.
Coordinator nodes route requests efficiently, reducing the workload on data nodes.
### Shard & Replica

An index is divided into multiple shards for scalability (AWS generally recommends shard sizes between 10â€“50 GB). Each shard can have one or more replicas to improve availability and fault tolerance.

### Inverted Index & BM25

Full-text search is powered by an inverted index, while result relevance is ranked using the BM25 algorithm, providing fast and accurate search experiences.

## Sample Application Architecture

A production-ready search application on AWS is typically designed using a multi-layer security architecture, where each component works together seamlesslyâ€”from the frontend to the data cluster.

## Detailed Request Flow

When users interact with the application, requests follow a clear sequence of steps:

### Step 1 â€“ Accessing the Frontend

Users access the application through AWS App Runner, which hosts and serves the frontend automatically.

### Step 2 â€“ Authentication

Amazon Cognito handles user authentication and authorization, ensuring that only legitimate users can access the system.

### Step 3 â€“ Routing Through API Gateway

All frontend requests pass through Amazon API Gateway, which serves as the single entry point for the application.

API Gateway validates Cognito-issued tokens and forwards authorized requests to AWS Lambda functions running inside the VPC.

### Step 4 â€“ Business Logic Processing with Lambda

Depending on the request type, AWS Lambda performs one of two primary tasks:

Indexing new data into OpenSearch
Executing search queries against the existing cluster
### Step 5 â€“ OpenSearch in a Secure Environment

The entire OpenSearch cluster resides within private subnets of a Virtual Private Cloud (VPC) and is never exposed directly to the public internet. This provides a critical layer of protection for sensitive business data.
![SÆ¡ Ä‘á»“ kiáº¿n trÃºc](/images/architecture.png)

## Conclusion

With this architecture, you can build a production-ready search application on AWS without managing complex infrastructure.

Amazon OpenSearch Service provides:

Fast and scalable search capabilities that grow with business demands
Built-in security and compliance features with minimal configuration
Automated cluster management, allowing AWS to handle operational complexity
Flexible pricing, ensuring you only pay for the resources you actually use

The complete source code and deployment guide are available on GitHub:

https://github.com/aws-samples/sample-for-amazon-opensearch-service-tutorials-101

You can clone the repository and start building your own search application today.

Original article:
https://aws.amazon.com/blogs/big-data/amazon-opensearch-service-101-create-your-first-search-application-with-opensearch/