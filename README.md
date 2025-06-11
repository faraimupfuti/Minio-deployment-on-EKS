# Minio-deployment-on-EKS
I've created a comprehensive CloudFormation template that deploys MinIO object storage on Amazon EKS. Here's what the template includes:
Key Components:
Infrastructure:

    VPC with public and private subnets across 2 AZs
    NAT Gateways for private subnet internet access
    Internet Gateway for public subnet access
    Route tables and security groups

EKS Cluster:

    EKS Cluster with version 1.29
    Managed Node Group with auto-scaling (2-5 nodes)
    EBS CSI Driver addon for persistent storage
    CloudWatch logging enabled

MinIO Deployment:

    MinIO container with latest image
    Persistent Volume (20Gi EBS storage)
    LoadBalancer Service exposing both API (9000) and Console (9001)
    Kubernetes Secret for MinIO credentials
    Health checks and resource limits

Supporting Services:

    Custom Storage Class optimized for MinIO
    Lambda function for managing Kubernetes resources via CloudFormation
    IAM roles with least-privilege permissions

Key Features:

    High Availability: Multi-AZ deployment with auto-scaling
    Security: Private subnets for worker nodes, proper IAM roles
    Storage: Persistent EBS volumes with GP3 storage class
    Monitoring: CloudWatch logging and health probes
    Access: LoadBalancer for external access to both API and web console

Usage:

    Deploy the stack with your preferred parameters
    Configure kubectl using the output instructions
    Access MinIO via the LoadBalancer endpoints
    Default credentials: minioadmin / minioadmin123

The template is production-ready and follows AWS best practices for EKS deployments. You can customize the parameters like instance types, node counts, and storage sizes based on your requirements.

