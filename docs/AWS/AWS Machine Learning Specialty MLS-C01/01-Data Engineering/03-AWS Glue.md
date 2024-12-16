
!!! important Glue Data Catalog
> - Metadata repository for all your tables:
> 	- Automated Schema Inference.
> 	- Schemas are versioned.
> - Integrates with Athena or Redshift Spectrum(schema & data discovery).
> - Glue Crawlers can help build the Glue Data Catalog.

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204112708.png)

!!! important Glue Data Catalog Crawlers
> Crawlers goes through your data to infer schemas and partitions.
> - Works JSON, Parquet, CSV, relational store.
> - Crawlers work for [S3](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), Redshift, [Amazon RDS](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md).
> - Need an IAM role/ credentials to access the data stores.


!!! important Glue and [S3 Partitions](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/01-Data%20Engineering/01-Amazon%20S3%20for%20Machine%20Learning.md)
> - Glue crawler will extract partitions based on how your S3 data is organized.
> - Think up front how you will be querying your data lake in S3.

---


!!! important Glue ETL
> - Transform data, Clean Data, Enrich Data(before doing analysis).
> 	- Generate ETL code in Python or Scala, you can modify the code.
> 	- Can provide your own Spark or PySpark scripts.
> 	- Target can be S3, JDBC([RDS](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md), Redshift), or in Glue Data Catalog.
> - Fully managed, cost effective, pay only for the resources consumed.
> - Jobs are run on a serverless Spark platform.
> - Glue Scheduler to schedule the jobs.
> - Glue Triggers to automate job runs based on "events".


!!! warning Glue ETL - Transformations
- Bundled Transformations:
	- DropFields, DropNullFields -> Remove(null) fields.
	- Filter -> Specify a function to filter records.
	- Join -> To enrich Data.
	- Map -> Add fields, delete fields, perform external lookups.
- Machine Learning Transformations:
	- FindMatches ML: Identify duplicate or matching records in your dataset, even when the records do not have a common unique identifier and no fields match exactly.

---

!!! important AWS Glue DataBrew
> - Allows you to clean and normalize data without writing any code.
> - Reduce ML and analytics data preparation time by up to 80%.
> - Data sources include [S3](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), Redshift, [Aurora](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/03-RDS,%20Aurora%20&%20ElastiCache/03-Amazon%20Aurora.md), Glue Data Catalog, ...
> - +250 ready-made transformations to automate tasks:
> 	- Filtering anomalies, data conversion, correct invalid values, ...
