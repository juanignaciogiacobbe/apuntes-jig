
!!! note AWS Data Pipeline
> - Destinations include [[AWS/Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|S3]], [[AWS/Cloud Practitioner CLF-C02/05-Storage and Databases/02-Amazon Relational Database Service RDS|RDS]], DynamoDB, Redshift and EMR.
> - Manages task dependencies.
> - Retries and notifies on failures.
> - Data sources may be on-premises.
> - Highly Available.

![[AWS/AWS Machine Learning Specialty MLS-C01/img/Pasted image 20241204114531.png]]

!!! warning AWS Data Pipeline VS Glue 
- Glue:
	- Glue ETL -> Run Apache Spark code, Scala or Python based, focus on the ETL.
	- Glue ETL -> Do not worry about configuring or managing the resources.
	- Data Catalog to make the data available to Athena or Redshift Spectrum.
- Data Pipeline:
	- Orchestation service.
	- More control over the environment, compute resources that run code, & code.
	- Allows access to [[AWS/Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]] or EMR instances(creates resources in your own account).
