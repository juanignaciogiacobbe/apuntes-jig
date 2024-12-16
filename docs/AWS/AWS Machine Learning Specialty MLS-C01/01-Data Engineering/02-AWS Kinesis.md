
> [!IMPORTANT] AWS Kinesis
> - Is a managed alternative to Apache Kafka.
> - Great for application logs, metrics, IoT, clickstreams.
> - Great for "real-time" big data.
> - Great for streaming processing frameworks.
> - Data is automatically replicated synchronously to 3 [AZ](AWS/Cloud%20Practitioner%20(CLF-C02)/03-Infrastructure%20and%20Realiability/02-Availability%20Zones.md).

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204101111.png)

---


> [!IMPORTANT] Kinesis Streams
> Low latency streaming ingest at scale.
> - Streams are divided in ordered Shards/Partitions.
> - Data retention is 24 hours by default, can go up to 365 days.
> - Ability to reprocess/replay data.
> - Multiple applications can consume the same stream.
> - Once data is inserted in Kinesis, it can't be deleted(immutability).
> - Records can be up to 1MB in size.

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204101410.png)


> [!NOTE] Kinesis Data Streams - Capacity Modes
> - Provisioned Mode:
> 	- You can choose the number of shards provisioned, scale manually or using API.
> 	- Each shard gets 1MB/s in(or 1000 records per second).
> 	- Each shard gets 2MB/s out(classic or enhanced fan-out consumer).
> 	- You pay per shard provisioned per hour.
> - On-demand Mode:
> 	- No need to provision or manage the capacity.
> 	- Default capacity provisioned(4MB/s in or 4000 records per second).
> 	- Scales automatically based on observed throughput peak during the last 30 days.
> 	- Pay per stream per hour & data in/out per GB.


---


> [!IMPORTANT] Kinesis Analytics
> Perform real-time analytics on streams using SQL.
> - Pay only for resources consumed(but it's not cheap).
> - Serverless: Scale automatically.
> - Use IAM permissions to access streaming source and destination(s).
> - SQL or Flink to write the computation.
> - Schema discovery.
> - Lambda can be used for pre-processing.

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204103319.png)

> [!NOTE] Use Cases
> - Streaming ETL: Select columns, make simple transformations, on streaming data.
> - Continuous metric generation: Live leaderboard for a mobile game.
> - Responsive analytics: Look for certain criteria and build alerting(filtering).


> [!WARNING] Machine Learning on Kinesis Data Analytics

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204104046.png)

## Kinesis Data Analytics + Lambda
- AWS Lambda can be a destination as well.
- Allows lots of flexibility for post-processing.
	- Aggregating rows.
	- Translating to different formats.
	- Transforming and enriching data.
	- Encryption.
- Opens up access to other services & destinations:
	- S3, DynamoDB, Aurora, Redshift, SNS, SQS, CloudWatch.

---


> [!IMPORTANT] Kinesis Firehose
> - Fully managed service, no administration.
> - Near Real Time(Buffer based on time and size, optionally can be disabled).
> - Data Ingestion into Redshift/ [Amazon S3](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md), ElasticSearch / Splunk.
> - Automatic scaling.
> - Supports many data formats.
> - Data Conversions from CSV/ JSON to Parquet / ORC(only for S3).
> - Data Transformation through [AWS Lambda](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/06-AWS%20Lambda.md).
> - Supports compression when target is Amazon S3(GZIP, ZIP and SNAPPY).
> - Pay for the amount of data going through Firehose.

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204102047.png)

---


> [!IMPORTANT] Kinesis Video Streams
> Meant for streaming video in real-time.

![](AWS/AWS%20Machine%20Learning%20Specialty%20MLS-C01/img/Pasted%20image%2020241204104618.png)


