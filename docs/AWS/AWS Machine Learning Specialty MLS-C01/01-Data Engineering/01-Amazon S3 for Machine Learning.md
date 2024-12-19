
!!! note "[[01-Amazon Simple Storage Service S3|S3]] for Machine Learning"
> - It's the backbone for many AWS ML service(example: SageMaker).
> - Create a "data lake" -> Infinite size, no provisioning, 99.999999999% durability, and Decoupling of storage(S3) to compute.
> - Centralized Architecture.


!!! note "Amazon S3 Data Partitioning"
> Pattern for speeding up range queries.
> - You can define whatever partitioning strategy.
> - Data partitioning will be handled by some tools we use(e.g. AWS Glue).
