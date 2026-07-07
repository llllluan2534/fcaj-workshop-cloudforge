---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---


### Week 3 Objectives:

* Deep dive into AWS storage solutions by designing a highly available static web architecture with Amazon S3 and CloudFront.
* Explore managed relational databases to understand how Amazon RDS handles scaling, failover, and automated maintenance.
* Bridge the gap between compute and data layers by securely networking EC2 instances to RDS databases.
* Broaden networking knowledge by examining Amazon Lightsail's automated VPC provisioning and Site-to-Site VPN integrations.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:**<br>&emsp; + Learn about related concepts of Amazon S3 and its role in hosting static websites.<br>&emsp; + Understanding Block Public Access settings and public object permissions for security.<br>&emsp; + Enhancing website performance and global distribution using Amazon CloudFront.<br>&emsp; + Bucket versioning to manage multiple file versions and object replication across regions.<br>&emsp; + Reviewing best practices for S3 hosting (enforcing security, optimizing costs).<br>. | 01/05/2026 | 03/05/2026      |
| 3   |  - **Practice:**<br>&emsp; + Created and configured an S3 bucket, then enabled static website hosting.<br>&emsp; + Configured public permissions and tested the website via the S3 endpoint.<br>&emsp; + Integrated Amazon CloudFront with the S3 static website.<br>&emsp; + Enabled bucket versioning, practiced moving objects, and tested cross-region object replication.<br>&emsp; + Performed resource cleanup to avoid unnecessary costs                                            | 03/05/2026 | 03/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Learning Content:**<br>&emsp; + Amazon RDS, its benefits (backups, scaling, HA), and supported engines.<br>&emsp; + Understanding EC2 as a database client and configuring Security Groups for SSH (port 22) and MySQL (port 3306).<br>&emsp; + Launching RDS with MySQL, configuring Multi-AZ deployments, and installing database clients on EC2.<br>&emsp; + Monitoring database performance with CloudWatch and the importance of resource cleanup.<br> | 04/05/2026 | 04/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   |- **Practice:**<br>&emsp; + Created an EC2 instance, installed MySQL client, and verified SSH connectivity.<br>&emsp; + Launched a MySQL RDS instance with automatic backups and Multi-AZ enabled.<br>&emsp; + Configured Security Groups to allow EC2 to access RDS, connected to it, and ran SQL queries.<br>&emsp; + Monitored RDS metrics in CloudWatch and properly cleaned up all resources to avoid costs.                             | 05/05/2026 | 05/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Learning Content:**<br>&emsp; + Amazon Lightsail basics: simplified instances that automatically provision VPCs, subnets, and IPs for quick application deployments.<br>&emsp; + VPC & VPN Site-to-Site objectives: understanding VPC as an internal network and VPNs for connecting AWS to on-premise networks.<br>&emsp; + Identified VPN-related costs (connection-hour, data transfer, public IPv4).<br>&emsp; + Core concepts: VPC, Virtual Private Gateway, Customer Gateway, and high-bandwidth VPN connections. | 06/05/2026 | 06/05/2026      | <https://cloudjourney.awsstudygroup.com/> |


### Week 3 Achievements:


* Architected a secure, globally distributed static website utilizing Amazon S3 bucket policies and CloudFront CDN.
* Safeguarded data by configuring advanced S3 features, including object versioning and cross-region replication.
* Provisioned and operated a production-ready MySQL database on Amazon RDS, successfully testing Multi-AZ failovers.
* Established a reliable client-server architecture by configuring EC2 instances to securely communicate with RDS through custom Security Groups.
* Developed a strong conceptual grasp of hybrid cloud connectivity (Site-to-Site VPN) and simplified instance deployments via Amazon Lightsail.
