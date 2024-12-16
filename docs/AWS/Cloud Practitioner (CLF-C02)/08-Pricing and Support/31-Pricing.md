# How Pricing Works
- **Pay for what you use**: For each service, you pay for exactly the amount of resources that you actually use, without requiring long-term contracts or complex licensing.
- **Pay less when you reserve**: Some services offer reservation options that provide a significant discount compared to On-Demand Instance pricing. For example, suppose that your company is using Amazon EC2 instances for a workload that needs to run continuously. You might choose to run this workload on Amazon EC2 Instance Savings Plans, because the plan allows you to save up to 72% over the equivalent On-Demand Instance capacity.
- **Pay less with volume-based discounts when you use more**: Some services offer tiered pricing, so the per-unit cost is incrementally lower with increased usage. For example, the more Amazon S3 storage space you use, the less you pay for it per GB.

## AWS Pricing Calculator
- Lets you explore AWS services and create an estimate for the cost of your use cases on AWS. You can organize your AWS estimates by groups that you define. A group can reflect how your company is organized, such as providing estimates by cost center.
- When you have created an estimate, you can save it and generate a link to share it with others.

	![aws-pricing-calculator](../img/aws-pricing-calculator.png)

	- Suppose that your company is interested in using Amazon EC2. However, you are not yet sure which AWS Region or instance type would be the most cost-efficient for your use case. In the AWS Pricing Calculator, you can enter details, such as the kind of operating system you need, memory requirements, and input/output (I/O) requirements. By using the AWS Pricing Calculator, you can review an estimated comparison of different EC2 instance types across AWS Regions.

## AWS Pricing Examples

### [06-AWS Lambda](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/06-AWS%20Lambda.md)
- You are charged based on the number of requests for your functions and the time that it takes for them to run.
- AWS Lambda allows 1 million free requests and up to 3.2 million seconds of compute time per month.
- A request is counted each time it starts execution. Test invokes in the console count as well.
- You can save on AWS Lambda costs by signing up for a Compute Savings Plan. A Compute Savings Plan offers lower compute costs in exchange for committing to a consistent amount of usage over a 1-year or 3-year term. This is an example of **paying less when you reserve**.
- The free usage tier includes 1 million free requests each month.

#### Example
- If you have used AWS Lambda in multiple AWS Regions, you can view the itemized charges by Region on your bill. 
- In this example, all the AWS Lambda usage occurred in the Northern Virginia Region. The bill lists separate charges for the number of requests for functions and their duration. 
- Both the number of requests and the total duration of requests in this example are under the thresholds in the AWS Free Tier, so the account owner would not have to pay for any AWS Lambda usage in this month.

	![aws_lambda_pricing_example](../img/aws_lambda_pricing_example.png)

### [[AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2)]]
- You pay for only the compute time that you use while your instances are running.
- For some workloads, you can significantly reduce Amazon EC2 costs by using **Spot Instances**: Your requests are fulfilled only if capacity is available. For example, suppose that you are running a batch processing job that is able to withstand interruptions. Using a Spot Instance would provide you with up to 90% cost savings while still meeting the availability requirements of your workload.
- You can find additional cost savings for Amazon EC2 by considering Savings Plans and Reserved Instances.

#### Example
- The service charges in this example include details for the following items:
	- Each Amazon EC2 instance type that has been used
	- The amount of Amazon EBS storage space that has been provisioned
	- The length of time that Elastic Load Balancing (ELB) has been used
- In this example, all the usage amounts are under the thresholds in the AWS Free Tier, so the account owner would not have to pay for any Amazon EC2 usage in this month.

	![ec2_pricing_example](../img/ec2_pricing_example.png)

### [[AWS/Cloud Practitioner (CLF-C02)/05-Storage and Databases/01-Amazon Simple Storage Service(S3)]]
- For Amazon S3 pricing, consider the following cost components:
	- **Storage -** You pay for only the storage that you use. You are charged the rate to store objects in your Amazon S3 buckets based on your objects’ sizes, storage classes, and how long you have stored each object during the month.
	- **Requests and data retrievals -** You pay for requests made to your Amazon S3 objects and buckets. For example, suppose that you are storing photo files in Amazon S3 buckets and hosting them on a website. Every time a visitor requests the website that includes these photo files, this counts towards requests you must pay for.
	- **Data transfer -** There is no cost to transfer data between different Amazon S3 buckets or from Amazon S3 to other services within the same AWS Region. However, you pay for data that you transfer into and out of Amazon S3, with a few exceptions. There is no cost for data transferred into Amazon S3 from the internet or out to Amazon CloudFront. There is also no cost for data transferred out to an Amazon EC2 instance in the same AWS Region as the Amazon S3 bucket.
	- **Management and replication -** You pay for the storage management features that you have enabled on your account’s Amazon S3 buckets. These features include Amazon S3 inventory, analytics, and object tagging.

#### Example
- The AWS account in this example has used Amazon S3 in two Regions: Northern Virginia and Ohio. For each Region, itemized charges are based on the following factors:
	- The number of requests to add or copy objects into a bucket
	- The number of requests to retrieve objects from a bucket
	- The amount of storage space used

- All the usage for Amazon S3 in this example is under the AWS Free Tier limits, so the account owner would not have to pay for any Amazon S3 usage in this month.

	![aws_s3_pricing_example](../img/aws_s3_pricing_example.png)

## AWS Billing and Cost Management Dashboard
- Use it to pay your AWS bill, monitor your usage, and analyze and control your costs.
	- Compare your current month-to-date balance with the previous month, and get a forecast of the next month based on current usage.
	- View month-to-date spend by service.
	- View Free Tier usage by service.
	- Access Cost Explorer and create budgets.
	- Purchase and manage Savings Plans.
	- Publish AWS Cost and Usage Reports.