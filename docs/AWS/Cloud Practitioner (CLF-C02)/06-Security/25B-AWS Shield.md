# AWS Shield
- **Protects applications against DDoS attacks**. AWS Shield provides two levels of protection: Standard and Advanced.

## AWS Shield Standard
- Automatically protects all AWS customers at no cost. It protects your AWS resources from the most common, frequently occurring types of DDoS attacks.
- As network traffic comes into your applications, AWS Shield Standard uses a variety of analysis techniques to detect malicious traffic in real time and automatically mitigates it.

## AWS Shield Advanced
- Is a paid service that provides detailed attack diagnostics and the ability to detect and mitigate sophisticated DDoS attacks.
- It also integrates with other services such as Amazon CloudFront, [[AWS/Cloud Practitioner (CLF-C02|03-AWS Route 53]]/04-Networking/03-AWS%20Route%2053.md), and [[ELB)](AWS/Cloud Practitioner (CLF-C02|02-Elastic Load Balancing(ELB)]]/02-Compute%20in%20the%20Cloud/02-Elastic%20Load%20Balancing(ELB).md). Additionally, you can integrate AWS Shield with AWS WAF by writing custom rules to mitigate complex DDoS attacks.