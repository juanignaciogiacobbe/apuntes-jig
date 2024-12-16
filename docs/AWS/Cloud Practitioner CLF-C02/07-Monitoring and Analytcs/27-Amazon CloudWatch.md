# Amazon CloudWatch
- Web service that **enables you to monitor and manage various metrics and configure alarm actions based on data from those metrics**.
- CloudWatch uses metrics to represent the data points for your resources. AWS services send metrics to CloudWatch. CloudWatch then uses these metrics to create graphs automatically that show how performance has changed over time.

## CloudWatch Alarms
- With CloudWatch, **you can create alarms that automatically perform actions if the value of your metric has gone above or below a predefined threshold.**
- For example, suppose that your company’s developers [[AWS/Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2]] instances for application development or testing purposes. If the developers occasionally forget to stop the instances, the instances will continue to run and incur charges. 
- In this scenario, you could create a CloudWatch alarm that automatically stops an Amazon EC2 instance when the CPU utilization percentage has remained below a certain threshold for a specified period. When configuring the alarm, you can specify to receive a notification whenever this alarm is triggered.

## CloudWatch Dashboard
- Enables you to access all the metrics for your resources from a single location. For example, you can use a CloudWatch dashboard to monitor the CPU utilization of an Amazon EC2 instance, the total number of requests made to an [[AWS/Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3]] bucket, and more. You can even customize separate dashboards for different business purposes, applications, or resources.

	![[AWS/Cloud Practitioner CLF-C02/img/cloudwatch_dashboard.png]]