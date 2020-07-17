# AWS Developer: Getting Started
- Also see PS course AWS Developer: The Big Picture

## Welcome to AWS
### Introduction
- ...

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

## Getting Inside the Virtual Machine with EC2 and VPC
### Introduction
- EC2 is fundamental to many AWS services 
- Use Elastic IPs, load balancer and auto scaling groups
- Use VPC to connect and secure resources, configure subnets, restrict access from external traffic, connect to VPNs

### VPC Overview
- Use VPCs create virtual networks to separate resources from the rest of AWS and public traffic
- Create upto 5 VPCs per account
- Use Security Groups to configure access between resources using IP addresses and ports. Comfigure Security Group access for other Security Groups as well as by IP addresses
- Use Routing Tables and Network Access Control List to control traffic routing and filtering VPC
- Assign resources to subnets within a VPC - has its own CIDR block, Routing Table and Network Access Control List
- Subnet example: private and public subnets, using NAT gateway to configure traffic between subnets

### Creating a VPC
- 

## Hosting All the Things with S3
### Introduction
- S3 using AWS SDK
- Web app updates to store/retrieve site images from S3

### S3 Overview
- Store objects in specified region
- S3 object - file + metadata
- Buckets store objects and provides a (unique) URL namespace for bucket
- Object key: <path>/<filename>
- S3 access with Permissions or IAM Roles
- Cross-region replication (1 additional region only, otherwise use CloudFront)

### Creating an S3 Bucket
- Create bucket (unique bucket name)
- Amazon Policy Generator tool
- Add Bucket Policy for public access to site assets

### Updating Objects to S3
- Upload objects using Console, CLI or SDK
- `aws s3 cp ...`

### Connecting to S3 with Code
- remove protocol from updated filepaths in source files
- `s3.putObject()` JS SDK

### Working with CORS in S3
- Configure CORS on S3 bucket - target resource (S3 bucket) exists on separate origin than web app requesting the resource

### Accessing S3 with EC2
- EC2 instance needs credentials to access S3 buckets
- Assign IAM Role at EC2 launch configuration level of AMI instance


## A Tale of Two Databases With DynamoDB and RDS
...

### DynamoDB Overview
- Non-relational, NoSQL
- Table -> Items (PK required)
- Provisioned ThroughPut Capacity (4kb units)

### Deciding Between RDS and DynamoDB
- Storage (schema) Flexiblity vs Query Flexibility
- RDS - strict schemas, querying flexibility

### Creating a Table in DynamoDB
- Create a db with a PK

### Connecting to DynamoDB with Code
- Using AWS SDK
- Get all items -  `.scan()` returns upto 1Mb items at a time, call repeatedly to get all items
- Running from EC2 - add permissions to ec2 security role to access RDS and DynamoDb, allow access to RDS from EC2 instance by adding to RDS instance security group

## Automate Your App with Elastic Beanstalk and CloudFormation

### CloudFormation Overview
- provision resources using templates
- JSON document
- Stacks - create, update, delete
- Tools - CloudFormation designer, CloudFormer

### Provisioning Resources with CloudFormation
- CloudFromation service
- create, test, delete infrastructure stack

### Elastic Beanstalk Overview
- automate application deployment - scaling, monitoring, resource provisioning
- upload code to Elastic Beanstalk - it provisions resources and runs your app
- EB Application - select a platform, has one or more app versions, contains multiple environments

### Deploying an Application with Elastic Beanstalk
- Deployment steps;
  - Manual: upload new code to EC2 instance, create AMI, update Load config, update Auto Scaling Group, terminate out-of-date Instances
  - ELB: Just upload new code ("plant the beanstalk seed")
- Create ELB Application, create Environment (web vs. long-running)
- ELB uses CloudFormation behind-the-scenes

### Configuring an Elastic Beanstalk Env
- Add RDS, DynamoDB, ElasticBeanstalkWebTier access to EC2 Security Group
- Allow access to RDS db from EC2 instance Security Group
- Security changes requires restart of app servers from ELB dashboard

## Speeding Up with CloudFront and ElastiCache
### Introduction
- CloudFront and CloutFront distributation
- Elasticache engine options

### CloudFront Overview
- Improve latency
- Global CDN
- Auto routes requests to closest CloudFront edge to the user
- Integrates with EC2, S3, load balancers
- Edges "Objects" and proxies dynamic content to origin source
- CloudFront Distribution - a set of content edged with CloudFront (assigned a URL), provides content from one or more origins
- CloudFront Distribution Behaviours - caching behaviour based on path

### Edging Your App with CloudFront
- Create a Distribution, set ELB app as origin
- Can add origin custom header
- Customise Object caching
- Setup cookie forwarding
- Set Edge Locations

### Configuring a CloudFront Distribution
- Can add multiple origins to the CloudFront Distribution
- Configure Cache Behaviour by path patterns
- Statistics, reports - e.g. cache hits/misses; popular objects

### ElastiCache Overview
- ElastiCache Cluster
- Redis/Memcached options

### Configuring a Redis Cluster in ElastiCache
- Create Security Group for ElastiCache cluster (port 6379 and ec2 Security Group)
- t2.micro instance available in free tier
- Select VPC to add Redis instance to
- Select Security Group created above

### Interacting with ElastiCache in Code










