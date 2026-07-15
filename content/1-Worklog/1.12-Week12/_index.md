---
title: "Week 12 Worklog"
date: 2026-04-17
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

Perform End-to-End integration and testing of the entire system on the actual Staging Cloud environment to evaluate the readiness of the architecture before launching to Production. The goal is to detect and completely resolve "hidden Cloud infrastructure" errors such as IAM Roles, CORS, VPC Network, and real hardware limits.

**Target Branch:**
`main` (Staging environment)

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2   | - **Golden Flow Scenario Testing:** <br>&emsp; + Successfully upload a video file (> 5 minutes long) via the Staging UI. <br>&emsp; + Verify that App Runner receives the request and successfully triggers AWS Step Functions / ECS. <br>&emsp; + Verify that the WebSocket progress transmission to the Frontend is smooth and does not disconnect. <br>&emsp; + Verify that the Pipeline completes 100%. <br>- **Validate AWS IAM & Security:** <br>&emsp; + ECS Task successfully fetches the file from S3 without Access Denied errors. <br>&emsp; + App Runner successfully reads/writes to RDS. <br>&emsp; + App Runner successfully calls AWS Bedrock and SQS/Step Functions. | 07/06/2026 | 07/06/2026 | [Internal Docs](#) |
| 3   | - **Validate Frontend WaveSurfer & S3 CORS:** <br>&emsp; + Ensure the Asset Detail page loads the `stream_url` (S3 Presigned URL). <br>&emsp; + Verify the WaveSurfer library can fetch byte-range chunks from S3 without encountering CORS Policy errors or token timeouts. | 07/07/2026 | 07/07/2026 | [Internal Docs](#) |
| 4   | - **Test Connection Recovery & State Synchronization:** <br>&emsp; + Upload a long video, and as soon as processing reaches about 30%, completely close the browser tab. <br>&emsp; + Wait 2 minutes, then reopen the application. <br>&emsp; + Verify that the Frontend accurately recovers the state from the `ingest_jobs` array and continues tracking progress smoothly. | 07/08/2026 | 07/08/2026 | [Internal Docs](#) |
| 5   | - **Failure Testing (Error Scenarios & Recovery):** <br>&emsp; + Simulate ECS Task crash mid-process (e.g., out of memory). <br>&emsp; + Simulate AWS Bedrock timeout / Rate Limit. <br>&emsp; + Simulate Transcribe failure. <br>&emsp; + Simulate a missing S3 file. <br>&emsp; + Verify that the Retry and Catch mechanisms of Step Functions work correctly. | 07/09/2026 | 07/09/2026 | [Internal Docs](#) |
| 6   | - **Cost Validation & Performance Audit:** <br>&emsp; + Upload a 5-minute video and measure the actual costs generated on the AWS bill. Estimate the Cost/Video. <br>&emsp; + Check if App Runner auto-scales when flooded with requests. <br>&emsp; + Check CloudWatch Logs for any spam logs or hidden errors. | 07/10/2026 | 07/10/2026 | [Internal Docs](#) |

### Week 12 Achievements (Definition of Done - DoD):

* ✅ A 5-minute video is successfully processed, displaying accurate Waveform, Transcript, and Scenes 100% on the Cloud.
* ✅ Errors related to IAM Roles, S3 CORS, and VPC Network are completely resolved.
* ✅ The system perfectly recovers its state upon closing/reopening the browser tab.
* ✅ All error scenarios (Crash, Timeout) are properly caught and safe error alerts are sent to the UI.
* ✅ Cost Validation report (estimated cost/video) is finalized.
* ✅ Confirmed the entire system meets MVP Ready standards on AWS:
  * Initialized network infrastructure, security, and database on AWS.
  * Built an automated AI processing flow (SQS, Step Functions, Amazon Bedrock).
  * Set up a CI/CD pipeline to automatically deploy Backend/AI Worker to ECS Fargate.
  * Configured Load Balancer and successfully integrated the WebSocket flow.
  * Deployed Frontend (Amplify) and set up monitoring systems (CloudWatch, X-Ray).
  * Drafted Workshop documentation guiding the deployment of the entire project architecture.
