# Terraform AWS Infrastructure Project

This Terraform project is used to provision AWS infrastructure for different environments (dev, staging, production) using modules. It creates an EC2 instance, S3 bucket, DynamoDB table, and sets up proper security groups, key pairs, and backend for state management using S3 and DynamoDB.

## Project Structure
- **backend.tf**: Defines the remote backend configuration, using S3 and DynamoDB for state management.
- **provider.tf**: Sets up the AWS provider and region to provision resources.
- **ec2.tf**: Provisions an EC2 instance, including security groups and key pair setup.
- **dynamodb.tf**: Defines a DynamoDB table for the environment.
- **s3.tf**: Provisions an S3 bucket for the environment.
- **variable.tf**: Contains all variables used across the project.
- **output.tf**: Outputs important information such as EC2 instance public IP and ARN.
- **main.tf**: Calls modules to provision infrastructure for different environments (dev, staging, production).

## Tags Overview
- **Backend Variables**: Defines the S3 bucket and DynamoDB table for storing the Terraform state.
- **Backend Resources**: Creates the DynamoDB table and S3 bucket used as the backend for state locking and management.
- **dev**: Provisions infrastructure for the development environment.
- **prd**: Provisions infrastructure for the production environment.
- **stg**: Provisions infrastructure for the staging environment.
- **Provider**: Configures the AWS provider and region.
- **DynamoDB Table**: Provisions a DynamoDB table for application storage.
- **EC2**: Provisions EC2 instances, security groups, and key pair.
- **S3**: Provisions an S3 bucket for each environment.
- **Outputs**: Outputs useful information like public IP and ARN of the EC2 instance.

## Prerequisites
- **Terraform v1.0+** installed
- **AWS CLI** configured with proper credentials and access
- **SSH key pair** for EC2 instance

## Usage
1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/your-repo.git
   cd your-repo

##Initialize Terraform:

```bash
terraform init
## Apply the Terraform plan:

##For dev environment:
    ```bash
terraform apply -var="my_env=dev" -auto-approve
## For staging environment:
    ```bash
terraform apply -var="my_env=stg" -auto-approve
 ## For production environment:
    ```bash
terraform apply -var="my_env=prd" -auto-approve

View the outputs: After the apply is complete, you will get the following outputs:

###Public IP of the EC2 instance
- ARN of the EC2 instance
- Destroy the infrastructure: To tear down all the resources created:
```bash
terraform destroy

##Notes
The backend.tf configuration stores the Terraform state file in an S3 bucket and uses DynamoDB for state locking.
Modify the ami_id and instance_type in variable.tf if you need a different instance type or AMI.
Ensure that the S3 bucket names and DynamoDB table names are globally unique when working in multiple regions or accounts.


