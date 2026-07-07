---
title: "Week 5 Worklog"
date: 2024-05-16
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---



### Week 5 Objectives:

* Understand the operational mechanism of Amazon EC2 Auto Scaling Group (ASG) and Load Balancer in dynamically adjusting resources.
* Master the architecture for deploying a highly scalable FCJ Management application.
* Practice creating a Target Group, initializing an Auto Scaling Group, and configuring related policies.
* Integrate a Load Balancer into the ASG to distribute incoming traffic evenly across EC2 instances.
* Implement a monitoring system using CloudWatch and receive notifications via Amazon SNS upon resource changes.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Auto Scaling Group Overview: Automatically adjust EC2 instances based on actual demand, preventing waste. <br>&emsp; + FCJ Management App Intro: Analyze architecture for deploying the app across an ASG. | 05/14/2026 | 05/14/2026      | <https://000006.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Load Balancer & Target Group: Mechanism to distribute traffic to instances in an ASG. <br>&emsp; + Scaling & Monitoring: Use CloudWatch metrics to decide when to add/remove instances. <br>&emsp; + Notifications & Risks: Amazon SNS integration. | 05/15/2026 | 05/15/2026      | <https://000006.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Prepare VPC, subnets, Launch Template. <br>&emsp; + Create a Target Group (FCJ-Management-TG) via HTTP and register EC2 instances. <br>&emsp; + Create an Auto Scaling Group (FCJ-Management-ASG) connected to 3 public subnets. | 05/16/2026 | 05/16/2026      | <https://000006.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Network & Load Balancer Configuration: Select Attach to an existing load balancer, enable Health checks. <br>&emsp; + Scaling Configuration: Set Desired/Min/Max capacity (1/1/3) and gather CloudWatch metrics. <br>&emsp; + Setup SNS to send emails on events. | 05/17/2026 | 05/17/2026      | <https://000006.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Test & Adjust: Copy Load Balancer DNS to access FCJ Management. Change Desired capacity to observe ASG auto-scale and check SNS emails. <br>&emsp; + Cleanup: Delete ASG, Target Group, and Load Balancer to avoid extra charges. | 05/18/2026 | 05/18/2026      | <https://000006.awsstudygroup.com/> |


### Week 5 Achievements:

* Proficiently operated an Auto Scaling Group combined with a Load Balancer to ensure high availability for the FCJ Management application.
* Deeply understood and executed the process of creating a Target Group and connecting a Launch Template to an ASG.
* Mastered monitoring the system with CloudWatch and reacting to system notifications via Amazon SNS.
* Perfected skills in analyzing and handling situations where the system needs to scale out or scale in resources.
* Mastered complex resource cleanup steps when working with multiple linked AWS services simultaneously.
