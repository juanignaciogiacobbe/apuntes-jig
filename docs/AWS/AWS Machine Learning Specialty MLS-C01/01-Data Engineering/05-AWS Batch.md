
!!! important AWS Batch
> - Run batch jobs as [Docker](Ingeniería de Software I/17-Docker.md) images.
> - Dynamic provisioning of the instances([EC2](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2).md) & Spot Instances).
> - Optimal quantity and type based on volume and requirements.
> - No need to manage clusters, fully serverless.
> - You just pay for the underlying EC2 instances.
> - Schedule Batch Jobs using CloudWatch Events.
> - Orchestate Batch Jobs using AWS Step Functions.


!!! warning When to use Batch?
- For any computing job regardless of the job (must provide Docker image). 
- Resources are created in your account, managed by Batch.
- For any non-ETL related work, Batch is probably better.
