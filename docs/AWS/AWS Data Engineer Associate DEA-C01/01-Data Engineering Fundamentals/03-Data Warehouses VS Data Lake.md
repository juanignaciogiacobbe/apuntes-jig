## Data Warehouse
- A centralized repository optimized for analysis where data from different sources is stored in a structured format.
- Designed for complex queries and analysis.
- Data is cleaned, transformed and loaded(ETL process).
- Typically uses a star or snowflake schema.
- Optimized for read-heavy operations.
- Example: [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/18-Amazon Redshift|Amazon Redshift]].

![[AWS/AWS Data Engineer Associate DEA-C01/img/Pasted image 20250204143449.png]]


## Data Lake
- A storage repository that holds vast amounts of raw data in its native format, including structured, semi-structured and unstructured data.
- Can store large volumes of raw data without predefined schema.
- Data is loaded as-is, no need for preprocessing.
- Supports batch, real-time and stream processing.
- Can be queried for data transformation or exploration purposes.
- Example: [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|Amazon S3]] when used as a data lake.


## Data Warehouse VS Data Lake

|            | Data Warehouse                                                         | Data Lake                                                                                   |
| ---------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Schema     | On-Write(predefined schema before writing data).                       | Schema On-Read(schema defined at the time of reading data).                                 |
| Data Types | Primarily structured data.                                             | Both structured and unstructured data.                                                      |
| Agility    | Less agile due to predefined schema.                                   | More agile as it accepts raw data without a predefined structure.                           |
| Processing | ETL                                                                    | ETL or just load for storage purposes.                                                      |
| Cost       | Typically more expensive because of optimizations for complex queries. | Cost-effective storage solutions, but costs can rise when processing large amounts of data. |

## Data Lakehouse
- A hybrid data architecture that combines the best features of data lakes and data warehouses, aiming to provide the performance, reliability and capabilities of data warehouse while maintaining the flexibility, scale, and low-cost storage of data lakes.
- Supports both structured and unstructured data.
- Allows for schema-on-write and schema on-read.
- Provides capabilities for both detailed analytics and machine learning tasks.
- Typically built on top of cloud or distributed architectures.