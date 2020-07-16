# AWS Developer: Getting Started
- Also see PS course AWS Developer: The Big Picture

## Welcome to AWS
### Introduction
-

### Developing in the Cloud
#### Similarities
- App runs on an OS/platform
- Platform needs to be installed
- Ports need to be opened
- Connects to a database

#### Differences
- Everything locally on same machine Vs. One Service = One Responsibility
- Files stored on server Vs. Files served from S3
- Database on same server as application Vs. Database as a Service
- Connections done manually Vs. Connections done with AWS SDK

### The Web of Amazon Web Services
- Resource-based services accessed by locally-assigned IP address (or Amazon Resource Name) and port 
- Communicate with services over TCP (usually HTTP)
- Many services are founded on instances of the EC2 services

### AWS Tooling: Web Console
- Each service has its own dashboard

### AWS Tooling: CLI
- CLI supports all Web Console and SDK features

### AWS Tooling: Software Development Kits
- SDK provided as a simpler way to communicate with AWS services than just over TCP
- Multiple language SDKs available
- Course uses a Node.js project and therefore the JS SDK

### Who Luvs Pizza?
- Demo web app to be hosted on AWS
- Web app hosting - EC2
- Website assets - S3
- Users - DynamoDB
- Session cache - Elasticache
- Save created pizzas - RDS

### Installing Node.js
- Install Node.js 12

### Install the AWS CLI
- Install latest AWS CLI (may require restart to update PATH)
- `aws --version` check installation

### Creating and initialzing an AWS account
- Create AWS account
- Create AWS Access Key (can be easily created/deleted)
- `aws configure` configure AWS CLI with Access Key
- `aws ec2 describe-instances` test AWS CLI is configured with Amazon account

### Conclusion
- The AWS development experience
- The AWS web (of services)
- AWS Toolbox: Console, CLI, SDK
- Pizza demo app
- AWS dev setup

## Sounding the Alarm with IAM and Cloudwatch
### Introduction

### Cloudwatch Overview
- Monitor service resources
- Use to stop, restart, recover, scale services

### Simple Notfication Service (SNS)
- Use with Cloudwatch to send alerts by email, SMS

### Creating a CloudWatch Alarm
- Create a billing alarm to monitor estimated montlhly billing (billing alarms only available in N. Virginia region) and manage AWS costs

### Identity & Access Management Overview
- ...

### Securing Your Account
- Enable MFA

### Understanding Policies
- JSON format - effect, action, resource


### Configuring Users and Groups
- good practices: assign policies to groups and then add users to groups rather than assigning policies directly to users; use least privilege principle

### Conclusion
- ...
