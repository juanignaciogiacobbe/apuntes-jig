
> [!IMPORTANT] AWS Batch
> - Run batch jobs as [Docker](Ingeniería%20de%20Software%20I/17-Docker.md) images.
> - Dynamic provisioning of the instances([EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) & Spot Instances).
> - Optimal quantity and type based on volume and requirements.
> - No need to manage clusters, fully serverless.
> - You just pay for the underlying EC2 instances.
> - Schedule Batch Jobs using CloudWatch Events.
> - Orchestate Batch Jobs using AWS Step Functions.


> [!WARNING] When to use Batch?
- For any computing job regardless of the job (must provide Docker image). 
- Resources are created in your account, managed by Batch.
- For any non-ETL related work, Batch is probably better.
