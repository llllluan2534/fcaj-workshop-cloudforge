---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---


### Week 8 Objectives:

* Get familiar with AWS CLI and understand the correlation between CLI commands and AWS APIs.
* Successfully install and configure the AWS CLI on your personal OS (Windows, macOS, or Linux).
* Securely manage credentials (Access key ID, Secret access key) via the `.aws` directory instead of the root account.
* Practice operating multiple services (IAM, S3, EC2) directly from the command line.
* Master the steps to clean up credentials to ensure security.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + AWS CLI Overview: Command-line tool to manage AWS from the terminal, great for automation & DevOps. Each CLI command maps to an AWS API. <br>&emsp; + IAM user & credentials: It's mandatory to use an IAM user (Access/Secret keys), never root. Credentials are saved locally for authentication. | 06/18/2026 | 06/18/2026      | <https://000011.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + CLI Configuration: Use `configure` to set Access keys, region, and format. CLI automatically reads credentials from the local config directory. <br>&emsp; + Basic Commands: Check version, IAM identity (`sts get-caller-identity`); S3 ops (list, create, delete); EC2 ops (list regions/instances); IAM ops (list users/policies). | 06/19/2026 | 06/19/2026      | <https://000011.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Prepare IAM user & credentials: Create IAM user for CLI, generate Access Key, save ID/Secret Key and lab region. <br>&emsp; + Install AWS CLI: Download/install based on OS (Windows, macOS, Linux). Run version check in terminal to confirm. <br>&emsp; + Initial Configuration: Run `aws configure` to input credentials, region, format, and verify files. | 06/20/2026 | 06/20/2026      | <https://000011.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Verify Identity: Run IAM command to confirm account ID and ARN match the lab. <br>&emsp; + S3 Operations: List existing buckets, create a new S3 bucket (if required by lab), and verify by listing again. <br>&emsp; + EC2 Operations: List AWS regions, list EC2 instances in the current region, and view details of a specific instance. | 06/21/2026 | 06/21/2026      | <https://000011.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + IAM Operations: List IAM users, check policies attached to the current user to verify lab permissions. <br>&emsp; + Cleanup: Delete Access Key on the AWS Console for safety on public machines; delete local config files to remove credentials. | 06/22/2026 | 06/22/2026      | <https://000011.awsstudygroup.com/> |


### Week 8 Achievements:

* Successfully installed and configured the AWS CLI tailored to the personal operating system environment.
* Deeply understood authentication mechanisms via Access and Secret keys, ensuring best security practices.
* Gained confidence in managing resources remotely via the CLI for popular services (Amazon S3, Amazon EC2, IAM).
* Developed skills in reading CLI JSON outputs and using the `--query` parameter to extract specific data.
* Cultivated good risk management habits by disabling or deleting local credentials post-project.
