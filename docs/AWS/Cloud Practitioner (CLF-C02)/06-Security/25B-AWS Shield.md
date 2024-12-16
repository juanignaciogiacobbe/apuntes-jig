# AWS Shield
- **Protects applications against DDoS attacks**. AWS Shield provides two levels of protection: Standard and Advanced.

## AWS Shield Standard
- Automatically protects all AWS customers at no cost. It protects your AWS resources from the most common, frequently occurring types of DDoS attacks.
- As network traffic comes into your applications, AWS Shield Standard uses a variety of analysis techniques to detect malicious traffic in real time and automatically mitigates it.

## AWS Shield Advanced
- Is a paid service that provides detailed attack diagnostics and the ability to detect and mitigate sophisticated DDoS attacks.
- It also integrates with other services such as Amazon CloudFront, [03-AWS Route 53](AWS/Cloud Practitioner (CLF-C02)/04-Networking/03-AWS Route 53.md), and [02-Elastic Load Balancing(ELB)](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/02-Elastic Load Balancing(ELB).md). Additionally, you can integrate AWS Shield with AWS WAF by writing custom rules to mitigate complex DDoS attacks.