
!!! important AWS Data Pipeline
> - Destinations include [[AWS/Cloud Practitioner (CLF-C02|S3]]/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), [[AWS/Cloud Practitioner (CLF-C02|RDS]]/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md), DynamoDB, Redshift and EMR.
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
	- Allows access to [[AWS/Cloud Practitioner (CLF-C02|EC2]]/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) or EMR instances(creates resources in your own account).
