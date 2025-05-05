Terraform AWS S3 Bucket Configuration 

Project Overview 

This Terraform configuration creates a secure AWS S3 bucket with recommended best practices for production environments. The project demonstrates Infrastructure as Code (IaC) principles and AWS cloud resource management using Terraform. 

Features 

Creates an S3 bucket with a unique name 

Implements versioning for object recovery 

Configures server-side encryption (AES256) 

Manages public access settings 

Outputs bucket details for reference 

Prerequisites 

Before using this configuration, ensure you have: 

Terraform installed (v1.0+ recommended) 

AWS account with appropriate permissions 

AWS CLI configured with credentials 

Basic understanding of Terraform and AWS S3 

Configuration Details 

Provider Configuration 

terraform { 
  required_providers { 
    aws = { 
      source  = "hashicorp/aws" 
      version = "~> 5.0" 
    } 
  } 
} 
 
provider "aws" { 
  region = "eu-west-1"  # Change this to your desired region 
} 
  

Resources Created 

S3 Bucket 

Creates the base bucket resource 

Bucket name is configurable 

Versioning 

Enables versioning to maintain multiple versions of objects 

Helps with data recovery and change tracking 

Public Access Block 

Configures public access settings 

Default configuration blocks all public access 

Server-Side Encryption 

Enables AES256 encryption by default 

Ensures data at rest is encrypted 

Outputs 

The configuration outputs: 

Bucket name 

Bucket ARN (Amazon Resource Name) 

Usage Instructions 

Clone the repository or copy the Terraform configuration 

Modify the bucket name in aws_s3_bucket.my_bucket to a globally unique name 

Optionally change the AWS region in the provider configuration 

Initialize Terraform:terraform init 
  

Review the execution plan:terraform plan 
  

Apply the configuration:terraform apply 
  

Customization 

To customize this configuration: 

Change the bucket name by modifying the bucket parameter 

Adjust the AWS region in the provider block 

Modify public access settings in aws_s3_bucket_public_access_block 

Change encryption settings if needed 

Best Practices Implemented 

Versioning: Enabled for object recovery 

Encryption: Server-side encryption by default 

Public Access: Restricted by default 

Infrastructure as Code: Reproducible configuration 

Output Variables: Easy reference to created resources 

Clean Up 

To destroy all created resources: 

terraform destroy 





Deploy to AWS S3 - GitHub Actions Workflow 

This workflow deploys an S3 bucket using Terraform with manual confirmation.  

Features 

✅ Manual Trigger (workflow_dispatch) with confirmation prompt 

✅ AWS Authentication using secrets 

✅ Terraform Setup & Execution (init, plan, apply) 

✅ State Management (optional state backup in GitHub secrets)  

Usage 

Manually trigger the workflow in GitHub Actions.  

Type deploy to confirm execution. 

Secrets Required 

AWS_ACCESS_KEY_ID  

AWS_SECRET_ACCESS_KEY  

BUCKET_NAME  

Workflow Steps 

Checks out repository code  

Configures AWS credentials  

Installs Terraform   

(Optional) Restores Terraform state  

Runs terraform init, plan, and apply 

 

Note: Uncomment sections for state persistence if needed.  

🔹 Adjust variables/secrets as per your AWS setup. 

 
