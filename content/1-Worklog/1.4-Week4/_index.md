---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Gain a deep understanding of the architecture and advantages of the Managed Relational Database service, Amazon RDS.
* Master DB instance deployment models and learn how to select the appropriate Database Engine (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server).
* Practice creating, configuring, and securely connecting to Amazon RDS from network environments (VPC).
* Clearly understand cloud database security mechanisms through Security Groups and Network ACLs.
* Develop cost management skills by thoroughly cleaning up and deleting unused resources.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Amazon RDS Overview: Learn how AWS automates heavy administrative tasks such as provisioning, OS patching, backups, and monitoring. <br>&emsp; + DB Instance Architecture: Independent cloud database environments with flexible compute and storage configurations.| 05/07/2026   | 05/07/2026      | <https://000005.awsstudygroup.com/>       |
| 3   | - **Learning Content:** <br>&emsp; + Supported Database Engines: Evaluate the pros and cons of MySQL, PostgreSQL, MariaDB, SQL Server, and Oracle. <br>&emsp; + Connection Mechanisms: Network architecture within a VPC, and the role of endpoints and ports when connecting from applications or clients. | 05/08/2026   | 05/08/2026      | <https://000005.awsstudygroup.com/>       |
| 4   | - **Learning Content:** <br>&emsp; + Security and Access Control: The importance of isolating databases within private subnets. <br>&emsp; + Resource Cleanup: Understand the lifecycle of a DB instance, snapshots, and long-term cost management strategies. | 05/09/2026   | 05/09/2026      | <https://000005.awsstudygroup.com/>       |
| 5   | - **Practice:** <br>&emsp; + Environment Preparation: Survey and configure the VPC, Subnets, and Security Groups to ensure a secure network architecture. <br>&emsp; + Launch DB Instance: Select an engine (e.g., MySQL), configure the master username/password, specify the network and security group, and wait for the instance to become Available. | 05/10/2026   | 05/10/2026      | <https://000005.awsstudygroup.com/>       |
| 6   | - **Practice:** <br>&emsp; + Connect to the Database: Retrieve the endpoint from the console, use tools (like MySQL Workbench, DBeaver, or terminal) to connect, and run basic SQL queries. <br>&emsp; + Optimize Security: Refine Security Groups to only open ports to necessary IPs/Instances. <br>&emsp; + Resource Cleanup: Delete the entire DB instance and associated manual snapshots to optimize costs. | 05/11/2026   | 05/11/2026      | <https://000005.awsstudygroup.com/>       |


### Week 4 Achievements:

* Proficiently understood and applied the Amazon RDS service to establish relational databases in the AWS environment.
* Developed the capability to plan rigorous network and security configurations for databases using VPCs, Subnets, and Security Groups.
* Successfully launched a DB instance and performed connections and data queries via popular administrative tools.
* Gained profound insights into security principles: Never enable public access for databases unless strictly necessary, and adhere to the least privilege principle.
* Excellently completed the cleanup phase, ensuring no orphan resources were left behind to waste budget.
