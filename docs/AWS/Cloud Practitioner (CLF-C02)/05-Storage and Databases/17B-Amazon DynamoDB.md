# Amazon DynamoDB
- **A key-value database service**.
- It delivers single-digit millisecond performance at any scale.
- DynamoDB is [04-Serverless Computing](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/04-Serverless%20Computing.md), which means that **you do not have to provision, patch, or manage servers**. 
- You also do not have to install, maintain, or operate software.
- As the size of your database shrinks or grows, **DynamoDB automatically scales to adjust for changes in capacity while maintaining consistent performance**. This makes it a suitable choice for use cases that require high performance while scaling.
- Chooses Performance over Consistency while delivering reads. During a read, it will look for the nearest & most available storage location for fulfilling the read request.