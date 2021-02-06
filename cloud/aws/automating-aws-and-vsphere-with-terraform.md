# Automating AWS and vSphere with Terraform
https://app.pluralsight.com/courses/cf585444-67d1-4d93-8354-22cdf8b0fb4d/table-of-contents

## Automating with Terraform
### Introduction
- Automate a IT service request - the IaC way
Benefits of IaC
- Improved quality when infrastructure is code checked into a repo
- Speed due to automation
- Automated infrastructure enables developer innovation
- Terraform uses a declarative syntax
- Create a set of primitive tasks library that can be reused to achieve different provisions as required

### Demo
- `.tf` files
- run `terrform apply`

## Installing Terraform
### Installing Terraform
- Supports multiple OSs

### Installing Terraform on Windows
- Download and copy exe to C:\Apps\terraform
- Add C:\Apps\terraform to path: `$env:Path += ";C:\Apps\terraform"`
- Check installation with `terraform -version`

### Installing Terraform on Mac with HomeBrew
...

## Terraform Constructs
### Terraform Constructs and Providers
Constructs:
- Providers, Resources, Provisioners
Execution:
- Plan, Execute, Destroy

- Docs: www.terraform.io/docs/

### Terraform Resources
- `resource "aws_instance" "pluralsightExample"
- Component "Provider_Type" "(Terraform) Name"

### Terraform Provisioners and Execution
- "When a resource is initially created, provisioners can be executed to initialise that resource"
- Execute some commands in the bare resource that has been created
Terraform Execution:
- Plan `terraform plan`
- Execute `terraform apply`
- Destroy `terraform destroy`

## Using Terraform with AWS
### Using the AWS Provider
- Setup AWS account
- Create IAM User (with secret key and access key) download and safely store secret key

### Provisioning and Destroying AWS EC2 instances with Terraform
- configure `provider` "aws" and `resource` "aws_instance" in `base.tf`
- run `terraform plan` and `terraform apply` to provision ec2 instance 
- add tags to easily identify resources
- run `terraform destroy` to delete provisioned resources
