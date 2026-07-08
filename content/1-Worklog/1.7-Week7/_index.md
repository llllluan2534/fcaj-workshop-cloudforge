---
title: "Week 7 Worklog"
date: 2026-04-17
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Get acquainted with Route 53 Resolver, understanding how to use Outbound Endpoints, Inbound Endpoints, and Resolver Rules.
* Establish a Hybrid DNS system seamlessly bridging the AWS environment and the on-premise (or AWS Managed AD) environment.
* Configure unified DNS query routing, allowing both sides to resolve each other's internal domain names effortlessly.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Hybrid DNS & Route 53 Resolver Overview: Combining on-premise (or AD) DNS with AWS DNS. <br>&emsp; + Outbound Endpoint (Red Arrow): Allowing Route 53 Resolver to send outbound DNS queries. | 06/11/2026 | 06/11/2026      | <https://000010.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Resolver Rules (Forwarding rule): Defining rules to forward queries to target DNS servers via Outbound Endpoints. <br>&emsp; + Inbound Endpoint (Blue Arrow): Allowing external DNS systems to send queries into the VPC for Route 53 Resolver to answer. <br>&emsp; + DNS forwarding from on-prem/AD to AWS: Configuring rules on internal DNS. | 06/12/2026 | 06/12/2026      | <https://000010.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Environment Prep: Verify VPC, subnets, security groups, and available on-prem (or Managed AD) environments. <br>&emsp; + Create Outbound Endpoint: Name it, choose VPC, subnets, attach security group allowing port 53 (UDP/TCP), and ensure the "Operational" state. | 06/13/2026 | 06/13/2026      | <https://000010.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Create Resolver Rule forwarding to AD/on-prem DNS: Declare internal domain, point target IP to external DNS, and associate with VPC. <br>&emsp; + Create Inbound Endpoint: Configure to allow inbound UDP/TCP port 53 and note the IPs. <br>&emsp; + Configure DNS forwarding on on-prem/AD to point to the Inbound Endpoint. | 06/14/2026 | 06/14/2026      | <https://000010.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Validate Route 53 Private Hosted Zone: Ensure A/CNAME records correctly map to private IPs. <br>&emsp; + Test bi-directional resolution: Use nslookup/dig on AWS EC2 to query the on-prem domain (and vice versa). Troubleshoot if errors occur. | 06/15/2026 | 06/15/2026      | <https://000010.awsstudygroup.com/> |

### Week 7 Achievements:

* Grasped and practically applied a Hybrid DNS architecture connecting on-premise networks with the AWS environment.
* Deeply understood and proficiently deployed Inbound & Outbound Endpoints of the Amazon Route 53 Resolver.
* Mastered configuring Resolver Rules to accurately route multi-directional DNS queries (DNS Forwarding).
* Gained the ability to diagnose, troubleshoot, and resolve domain resolution issues across combined environments using tools like nslookup or dig.
* Ensured seamless and unified continuity for hybrid applications via a centralized domain resolution system.
