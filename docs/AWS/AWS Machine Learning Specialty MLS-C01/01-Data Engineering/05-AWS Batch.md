
!!! important AWS Batch
> - Run batch jobs as [[Ingeniería de Software I/17-Docker.md|Docker]] images.
> - Dynamic provisioning of the instances([[AWS/Cloud Practitioner (CLF-C02|EC2]]/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) & Spot Instances).
> - Optimal quantity and type based on volume and requirements.
> - No need to manage clusters, fully serverless.
> - You just pay for the underlying EC2 instances.
> - Schedule Batch Jobs using CloudWatch Events.
> - Orchestate Batch Jobs using AWS Step Functions.


!!! warning When to use Batch?
- For any computing job regardless of the job (must provide Docker image). 
- Resources are created in your account, managed by Batch.
- For any non-ETL related work, Batch is probably better.
