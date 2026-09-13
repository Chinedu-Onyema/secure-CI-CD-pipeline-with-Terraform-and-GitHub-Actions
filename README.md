[![Terraform CI/CD with GitHub Actions](https://github.com/Chinedu-Onyema/CI-CD-for-IAC-with-terraform-GitHub-Actions/actions/workflows/deploy.yml/badge.svg)](https://github.com/Chinedu-Onyema/CI-CD-for-IAC-with-terraform-GitHub-Actions/actions/workflows/deploy.yml)

[![Terraform Infrastructure Cleanup](https://github.com/Chinedu-Onyema/CI-CD-for-IAC-with-terraform-GitHub-Actions/actions/workflows/cleanup.yml/badge.svg)](https://github.com/Chinedu-Onyema/CI-CD-for-IAC-with-terraform-GitHub-Actions/actions/workflows/cleanup.yml)


# DevSecOps CI/CD Pipeline for Infrastructure as Code (IaC) with Terraform & GitHub Actions

This is a comprehensive DevSecOps pipeline repository for automating infrastructure provisioning on AWS using Terraform, GitHub Actions, and continuous security/linting controls (TFLint and tfsec).
Remote state is securely managed using an S3 backend with state locking.

### PDF GUIDE: [CICD PIPELINE FOR IAC  WITH TERRAFORM.pdf](https://github.com/user-attachments/files/32160626/CICD.PIPELINE.FOR.IAC.WITH.TERRAFORM.pdf)


### WATCH VIDEO WALKTHROUGH HERE: https://youtu.be/3ggYdEdbBUA


## PREREQUISITES

An active AWS Account with permissions to manage S3 buckets and IAM credentials.  

A GitHub Account to host the repository and run GitHub Actions workflows.  

AWS Access Key ID and Secret Access Key configured for GitHub Secrets


## STEP-BY-STEP IMPLEMENTATION

### Phase 1: Environment Setup in GitHub Codespaces

1) Create an AWS S3 bucket for your state file remote backend (e.g., tfstate-140023390772-s3-bucket).

2) Create a GitHub repository named CICD-for-IAC-with-terraform-GitHub-Actions and launch a GitHub Codespace on main.

3) Run the following commands to install Terraform, AWS CLI, tfsec, and tflint:

#### Install Terraform CLI
<PRE>curl -fsSL https://releases.hashicorp.com/terraform/1.15.7/terraform_1.15.7_linux_amd64.zip -o terraform.zip</PRE>
<PRE>unzip terraform.zip</PRE>
<PRE>sudo mv terraform /usr/local/bin/</PRE>
<PRE>rm terraform.zip</PRE>
<PRE>terraform version</PRE>

#### Install AWS CLI v2
<PRE>curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"</PRE>
<PRE>unzip awscliv2.zip</PRE>
<PRE>sudo ./aws/install</PRE>
<PRE>rm awscliv2.zip</PRE>
<PRE>aws --version</PRE>

#### Authenticate AWS CLI
<PRE>aws configure</PRE>
<PRE>aws sts get-caller-identity</PRE>

#### Install Security Tools
<PRE>curl -s https://raw.githubusercontent.com/aquasecurity/tfsec/master/scripts/install_linux.sh | bash</PRE>
<PRE>tfsec --version</PRE>

<PRE>curl -s https://raw.githubusercontent.com/terraform-linters/tflint/master/install_linux.sh | bash</PRE>
<PRE>tflint --version</PRE>


### Phase 2: Remote Backend Configuration

1) Create backend.tf file to configure S3 remote state tracking and locking. Use backend.tf for in this repo:

Initialize backend initialization:

<PRE>terraform init</PRE>


### Phase 3: Infrastructure Code & Compliance Hardening

1) Create main.tf to provision an encrypted, private, and secure S3 bucket complying with tflint and tfsec rules:

<PRE>tflint</PRE>
<PRE>tfsec</PRE>


### Phase 4: DevSecOps CI/CD Pipeline Setup

1) Create .github/workflows/deploy.yml to define continuous integration and deployment automation:



### Phase 5: GitHub Actions Authentication (Secrets Setup)

1) Navigate to Settings -> Secrets and variables -> Actions in your GitHub Repository.

2) Click New repository secret and add:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

3) Commit and push your code to trigger the GitHub Actions workflow execution:

<PRE>git add .</PRE>
<PRE>git commit -m "Configure DevSecOps CI/CD pipeline"</PRE>
<PRE>git push</PRE>



### Phase 6: Automated Infrastructure Cleanup

1) To safely manage environment costs, define .github/workflows/cleanup.yml for scheduled or manual infrastructure teardowns:


## VERIFICATION & STATUS BADGES

1) AWS S3 State Verification: Verify state storage via AWS CLI inside Codespaces:

<PRE>aws s3 ls s3://tfstate-140023390772-s3-bucket/lock/</PRE>

Workflow Status Badges: Add workflow badges from the GitHub Actions tab to track deployment and cleanup health directly from README.md





