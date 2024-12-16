
!!! important AWS Data Pipeline
> - Destinations include [S3](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), [RDS](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md), DynamoDB, Redshift and EMR.
> - Manages task dependencies.
> - Retries and notifies on failures.
> - Data sources may be on-premises.
> - Highly Available.

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204114531.png)

!!! warning AWS Data Pipeline VS Glue 
- Glue:
	- Glue ETL -> Run Apache Spark code, Scala or Python based, focus on the ETL.
	- Glue ETL -> Do not worry about configuring or managing the resources.
	- Data Catalog to make the data available to Athena or Redshift Spectrum.
- Data Pipeline:
	- Orchestation service.
	- More control over the environment, compute resources that run code, & code.
	- Allows access to [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) or EMR instances(creates resources in your own account).
