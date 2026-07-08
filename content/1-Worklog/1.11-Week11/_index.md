---
title: "Week 11 Worklog"
date: 2026-04-17
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Deep dive into Amazon S3, exploring the object storage architecture and its real-world applications.
* Master advanced concepts such as Versioning, Storage Classes, and the pricing mechanism.
* Practice creating buckets, managing objects, and setting up permissions using IAM and Bucket Policies.
* Configure and experience data security features through encryption and Presigned URLs.
* Execute a systematic resource cleanup to ensure no data leaks and to tightly control costs.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Deep overview of Amazon S3: Object storage architecture, 99.999999999% (11 9s) durability, and real-world use cases. <br>&emsp; + Bucket and Object concepts: Naming conventions, global uniqueness, and choosing the optimal AWS Region for cost-efficiency. | 05/21/2026 | 05/21/2026      | <https://000057.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + S3 Storage Classes: Analyzing S3 Standard, Intelligent-Tiering, Glacier, and selecting the right class. <br>&emsp; + Lifecycle Policies: Automating data transitions and deletions over time to optimize costs. | 05/22/2026 | 05/22/2026      | <https://000057.awsstudygroup.com/> |
| 4   | - **Learning Content:** <br>&emsp; + Security and Permissions: Differences between IAM Policies, Bucket Policies, and ACLs. <br>&emsp; + Block Public Access mechanisms and the application of Presigned URLs for secure, temporary file sharing. | 05/23/2026 | 05/23/2026      | <https://000057.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Create an S3 bucket with standard security configurations; experiment with enabling/disabling Versioning to track file changes. <br>&emsp; + Upload, download, and configure metadata for objects. Update files to observe how S3 stores multiple versions. | 05/24/2026 | 05/24/2026      | <https://000057.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Establish a Bucket Policy to grant read-only access and test anonymous file downloads to verify permissions. <br>&emsp; + Generate Presigned URLs via CLI/Console to share files with time-limited access. <br>&emsp; + Resource Cleanup: Practice deleting objects (including hidden versions) and completely deleting buckets. | 05/25/2026 | 05/25/2026      | <https://000057.awsstudygroup.com/> |


### Week 11 Achievements:

* Gained profound knowledge of the object storage model, Storage Classes, and S3 Versioning.
* Successfully built a static storage system integrated with granular access control via Bucket Policies and IAM.
* Gained hands-on experience in securely sharing data with time restrictions using Presigned URLs.
* Mastered the lifecycle management of resources, from initialization and version control to thorough cleanup.
* Ensured a solid foundation for utilizing S3 as a primary storage layer for future Data Lake and Web Hosting architectures.
