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

## Using Local and Remote Exec
...

## Terraform Variables and Modules
### Using Variables in Terraform
- `user = "${var.vsphere_user}"
- create `variables.tf`
```
variable "vsphere_user" {
  description = "vSphere Username"
}
```
- running next `terraform plan" will prompt for variable values
- alternatively, create a `terraform.tfvars` file (convention filename)
```
vsphere_user = "username"
```
- can load variables from command line, from file (e.g. terraform.tfvars), from environment variables or provide default values if no other values are provided

### Using Modules in Terraform
- Store reusable code
- Include using `module` statement
- use a module with (e.g. in `dev.tf`):
```
provider "aws" {
  access_key = "${var.access_key}"
  secret_key = "${var.secret_key}"
  regon = "${var.region}"
}

module "base" {
  source = "../base"
}
```
- run `terraform get` to retrieve modules in a plan before running `plan` or `apply` command

## Code Control and Provisioners
### Code Control and Local Provisioners
GitHub Essentials
- add a .gitignore entry for `.tfstate` files
Local Provisioner (execute commands on the host machine that terraform is run on)
e.g. add the following to a resource...
```
  provisioner "local-exec" {
    command = "echo ${aws_instance.PluralServer.private_ip} >> private_ips.txt"
  }
```

### Remote Provisioners and Use Cases
- execute commands on the provisioned resource
e.g. change `"local-exec"` to `"remote-exec`
```
  provisioner "local-exec" {
    inline = [
      "puppet apply"
      "touch test.txt"
      ]
  }
```
- 3 types: `inline`, `script` or `scripts`
- remote scripts run over SSH so need to ensure this port is accessible on the remote host





