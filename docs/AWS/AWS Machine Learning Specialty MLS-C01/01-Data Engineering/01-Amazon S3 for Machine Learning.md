
> [[AWS/Cloud Practitioner (CLF-C02|!IMPORTANT]]/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md) for Machine Learning
> - It's the backbone for many AWS ML service(example: SageMaker).
> - Create a "data lake" -> Infinite size, no provisioning, 99.999999999% durability, and Decoupling of storage(S3) to compute.
> - Centralized Architecture.


!!! important Amazon S3 Data Partitioning
> Pattern for speeding up range queries.
> - You can define whatever partitioning strategy.
> - Data partitioning will be handled by some tools we use(e.g. AWS Glue).
