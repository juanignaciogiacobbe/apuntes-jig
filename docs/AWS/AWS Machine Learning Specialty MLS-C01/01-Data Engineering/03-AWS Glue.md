
!!! important Glue Data Catalog
> - Metadata repository for all your tables:
> 	- Automated Schema Inference.
> 	- Schemas are versioned.
> - Integrates with Athena or Redshift Spectrum(schema & data discovery).
> - Glue Crawlers can help build the Glue Data Catalog.

![[AWS/AWS Machine Learning Specialty MLS-C01/img/Pasted image 20241204112708.png]]

!!! important Glue Data Catalog Crawlers
> Crawlers goes through your data to infer schemas and partitions.
> - Works JSON, Parquet, CSV, relational store.
> - Crawlers work for [[AWS/Cloud Practitioner (CLF-C02|S3]]/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), Redshift, [[AWS/Cloud Practitioner (CLF-C02|Amazon RDS]]/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md).
> - Need an IAM role/ credentials to access the data stores.


> [[AWS/AWS Machine Learning Specialty MLS-C01/01-Data Engineering/01-Amazon S3 for Machine Learning.md|!IMPORTANT]]
> - Glue crawler will extract partitions based on how your S3 data is organized.
> - Think up front how you will be querying your data lake in S3.

---


!!! important Glue ETL
> - Transform data, Clean Data, Enrich Data(before doing analysis).
> 	- Generate ETL code in Python or Scala, you can modify the code.
> 	- Can provide your own Spark or PySpark scripts.
> 	- Target can be S3, JDBC([[AWS/Cloud Practitioner (CLF-C02|RDS]]/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md), Redshift), or in Glue Data Catalog.
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
> - Data sources include [[AWS/Cloud Practitioner (CLF-C02|S3]]/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), Redshift, [[AWS/AWS Solutions Architect Associate Certification SAA-C03/03-RDS, Aurora & ElastiCache/03-Amazon Aurora.md|Aurora]], Glue Data Catalog, ...
> - +250 ready-made transformations to automate tasks:
> 	- Filtering anomalies, data conversion, correct invalid values, ...
