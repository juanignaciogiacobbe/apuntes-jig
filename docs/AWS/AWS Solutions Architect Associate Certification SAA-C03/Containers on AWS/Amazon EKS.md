# Amazon Elastic Kubernetes Service(EKS)
- Launch managed Kubernetes clusters on AWS.
- Kubernetes is an open-source(cloud agnostic) system for automatic deployment, scaling and management of containerized application. -> An alternative to ECS, similar goal but different API.
- EKS supports [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]] if you want to deploy worker nodes or Fargate to deploy serverless container.
- For multiple regions, deploy one EKS cluster per region.
- Collect logs and metrics using [[AWS/AWS Cloud Practitioner CLF-C02/07-Monitoring and Analytcs/27-Amazon CloudWatch|CloudWatch]] Container Insights.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250113155842.png]]

---

## Node Types

#### Managed Node Groups
- Creates and manages Nodes(EC2 instances) for you.
- Nodes are part of an [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/05-Auto Scaling Group|ASG]] managed by EKS.
- Supports On-Demand or Spot Instances.

#### Self-Managed Nodes
- Nodes created by you and registered to the EKS cluster and managed by an ASG.
- You can use prebuilt [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI|AMI]] - Amazon EKS Optimized AMI.
- Supports On-Demand or Spot Instances.

#### AWS Fargate
- No maintenance required -> No nodes managed.

---

## Data Volumes
- Need to specify StorageClass manifest on your EKS Cluster.
- Leverages a Container Storage Interface(CSI) compliant driver.
- Support for [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS|EBS]], [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/04-Amazon EFS|EFS]], FSx for Lustre/NetApp ONTAP.
