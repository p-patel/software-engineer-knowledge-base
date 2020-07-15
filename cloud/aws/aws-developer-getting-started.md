# AWS Developer: Getting Started
- See also AWS Developer: The Big Picture

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







