# ETL Pipelines
- ETL: Extract, Transform and Load. -> Process used to move data from source systems into a [[AWS/AWS Data Engineer Associate DEA-C01/01-Data Engineering Fundamentals/03-Data Warehouses VS Data Lake|Data Warehouse]].

## Extract
- Retrieve data from source systems, which can be databases, CRMs, flat files, APIs, or other data repositories.
- Ensure data integrity during the extraction phase.
- Can be done in real-time or in batches, depending on requirements.

## Transform
- Convert the extracted data into a format suitable for the target data warehouse.
- Can involve various operations such as data cleaning, data enrichment, format changes, aggregations or computations, encoding or decoding data and handling missing values.

## Load
- Move the transformed data into the target data warehouse or another data repository.
- Can be done in batches(all at once) or in a streaming manner(as data becomes available).
- Ensure that data maintains its integrity during the loading phase.


---

## Managing ETL Pipelines
- This process must be automated in some reliable way.
- [[AWS/AWS Machine Learning Specialty MLS-C01/01-Data Engineering/03-AWS Glue|AWS Glue]].
- Orchestation services: [[AWS/AWS Solutions Architect Associate Certification SAA-C03/Monitoring, Audit and Performance/Amazon EventBridge|Amazon EventBridge]], [[AWS/AWS Machine Learning Specialty MLS-C01/01-Data Engineering/07-AWS Step Functions|AWS Step Functions]], [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/06-AWS Lambda|AWS Lambda]], Glue Workflows.
