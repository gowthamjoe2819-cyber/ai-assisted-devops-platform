DAY -1
# AI-Assisted Cost-Aware DevOps Platform

Goal:
Build a production-style AWS system with Terraform, CI/CD, monitoring, cost controls,
and AI-assisted log & cost analysis.

Architecture:
User → Load Balancer → App (EC2/ECS) → DynamoDB

Key Focus:
- Infrastructure as Code
- Automated deployment
- Cost visibility
- AI used only where it saves time or money

- 📅 Day 2 – Terraform Setup & Validation
🎯 Objective

Set up Terraform in the development environment, configure the AWS provider, and validate the infrastructure workflow without provisioning any resources.

✅ Tasks Completed

Verified AWS authentication using STS

Installed and configured Terraform

Defined Terraform provider and version constraints

Initialized Terraform working directory

Validated setup using terraform plan

Ensured no unintended infrastructure changes

Cleaned up Terraform cache and disk usage in CloudShell

Successfully committed and pushed Day 2 changes to GitHub

📂 Files Involved
infra/
├── main.tf
├── variables.tf
├── outputs.tf

🧩 Terraform Provider Configuration

Provider: AWS

Region: us-east-1

Terraform Version: >= 1.3.0

AWS Provider Version: ~> 5.0

🧪 Validation Output
terraform plan


Result:

No changes. Your infrastructure matches the configuration.


This confirms:

Terraform is correctly installed

AWS credentials are valid

State management is functioning

No infrastructure drift exists

🧠 Key Learnings

Terraform initialization must be completed before planning or applying

terraform plan is a safe, read-only validation step

CloudShell has storage limits and is best suited for short-lived tasks

Cleaning .terraform/ directories is safe and sometimes necessary

Git history should be kept clean using git pull --rebase

🔒 Best Practices Followed

No resources applied prematurely

No hardcoded credentials

No force pushes to GitHub

📅 Day 3 – VPC Design & Terraform Planning
🎯 Objective

Design a production-ready AWS VPC using Terraform and validate the infrastructure plan without applying any resources.

🏗️ Architecture Designed
VPC (10.0.0.0/16)
├── Public Subnet (10.0.1.0/24)
│   └── Internet Gateway
├── Private Subnet (10.0.2.0/24)
└── Route Tables


This layout represents a standard, scalable AWS networking foundation used in real-world environments.

✅ Tasks Completed

Moved Terraform execution to a dedicated EC2 dev instance

Designed VPC CIDR and subnet structure

Created public and private subnets

Attached Internet Gateway to the VPC

Configured public route table and subnet association

Defined Terraform outputs for core networking resources

Validated configuration using terraform plan

Properly excluded Terraform cache and state files from Git

Successfully committed and pushed clean Terraform code to GitHub

📂 Files Modified
infra/
├── main.tf
├── variables.tf
├── outputs.tf

🧩 Key Terraform Resources

aws_vpc

aws_subnet (public & private)

aws_internet_gateway

aws_route_table

aws_route_table_association

🧪 Validation Performed
terraform fmt
terraform validate
terraform plan


Result:

Plan: X to add, 0 to change, 0 to destroy


This confirms the VPC design is correct and ready to be applied safely.

🛑 Important Git & Terraform Practice

During Day 3, a common Terraform mistake was encountered and resolved:

Terraform provider binaries inside .terraform/ were accidentally staged

GitHub rejected the push due to file size limits

The issue was fixed by:

Adding .terraform/ to .gitignore

Removing cached files from Git

Amending the commit cleanly

This reinforces a critical best practice:

Terraform cache directories and state files should never be committed to version control.

🧠 Key Learnings

Terraform must be executed from the directory containing .tf files

Infrastructure should always be planned before applied

.terraform/ and *.tfstate must be excluded from Git

EC2 dev instances are more suitable than CloudShell for IaC work

Clean Git history matters in production environments

🔒 Best Practices Followed

No premature terraform apply

No hardcoded credentials

No large binaries committed

No force pushes to GitHub

Clean, reviewable Terraform plan

Clean commit history
