## AWS Services and Integrations

### Core AWS Services
- RDS
- Lambda
- Step Function
- Glue
- AWS Batch
- Athena
- Event Bridge
- CloudFormation
- Glue Workflows

### AWS Service Combinations
#### ✅ Confirmed Integrations
- RDS + CloudWatch + SNS ✅
- Lambda + API Gateway ✅
- Step Function + Lambda ✅
- Step Function + Lambda + SNS ✅
- Step Function + Lambda + EMR + S3 ✅

#### Step Function Integrations
- Step Function + RDS + SNS + Lambda
- Step Function to run ECS Task

#### Glue Integrations
- Glue + ETL + S3 Bucket Data + Scheduler
- Glue + Step Function + SNS
- Glue Workflows + ETL Job
- Glue + SNS + AWS Batch
- Glue + Step Function + SNS + S3 + Glue + RDS

#### AWS Batch Integrations
- AWS Batch + S3/ECR
- EC2 + AWS Batch + S3

#### Athena Integrations
- Athena + S3 + Fargate Task

#### Event Bridge Integrations
- Event Bridge + SES
- Event Bridge + API Gateway + AWS Kendra + S3
- CloudFormation + Event Bridge + EC2

#### CloudFormation Integrations
- CloudFormation + S3
- CloudFormation + Event Bridge + SES

#### ECS & Fargate Integrations
- ECS + Fargate Task + ALB
- ECS + Fargate Task + ALB + Two Container Endpoint

#### EC2 Integrations
- EC2 + AWS Batch + S3
- EC2 + RDS + CloudWatch + SNS
- EC2 + RDS (Connection) + SNS
- EC2 + Docker Images (2 Endpoints) + ALB
- EC2 + Boto3 + CloudWatch

#### Security & Compliance
- WAF + Lambda + API Gateway (Project API)
- S3 + EMR (Encryption In Transit and At Rest)
- IAM + Boto3 + SES + S3
- KMS + RDS + S3
- S3 + KMS + CloudFront: Secure Content Distribution
- SQS + Lambda + KMS: Secure Message Processing
- EBS + KMS + Lambda: Secure Snapshots and Backup Management
- API Gateway + Cognito + Lambda
- RDS + KMS + CloudTrail: Secure and Monitor Database Access
- CloudWatch + EventBridge + Lambda: Auto-Healing EC2 Instances

#### CI/CD & DevOps
- CI/CD Pipeline + S3 + ReactJS App + ALB
- Bitbucket + CI/CD Pipeline + S3 + ReactJS App
- Bitbucket/S3 + CI/CD Pipeline (Create IAM Role)
- CICD Pipeline (Create Any Python Code Repo)
- SAM + CI/CD Pipeline

#### AI & Data Processing
- SageMaker
- SageMaker + Any AWS Service
- ETL + Load Data from S3 + RDS
- ETL + Load Data from AWS Glue, S3 + RDS
- SNS + Lambda + EMR
- SNS + Lambda + EMR + S3
- Apache Airflow
- AWS Kendra + S3 + API Gateway

#### Pending Tasks
- Pending Task Complete (Multiple Instances)
