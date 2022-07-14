https://skillbuilder.aws/  for free learning AWS

Some questions commonly asked in AWS SAA- CO2 Solution Archi Exam:
  
When using AWS for R&D ahead of planned migration, how do you prevent unexpected increases or spikes in billing?
**1.  Using Root AWS acc, enable billing alerts in user preferences. Then use CloudWatch to create billing alarm & set threashold to specific dollar amount for your est monthly charges.**

2.  Using Root AWS acc, activate IAM access to billing information for account. Ensure your IAM user have BillingFullAccess Group Policy. Then from billing dashboard, check accrued charge once a day.
3.  Use bill dashboard to create cost budget. Input max amount you want to be charged each mo. Any charges that occur over this amount will cause AWS to auto suspend these resources.

4.  If you are using AWS free tier, you will have to confirm usage of any service that goes over AWS free tier limits.
Correct ans : 1

---
When launching EC2 instance with instance type that supports instance storage, what use case best for instance storage?
1. Instance storage is faster than EBS vol. so, install root of operating sys on this vol to speed up server performance.
2. USe instance storage to serve temp files that require low I/O latency.
3. USe instance storage to handle files uploaded by your users. Since its more secure than EBS vol, you can isolate any malicious fies from infecting your server. (X)
 
---
 When creating new EC2 instance, we can access it from public internet BY auto-assigning to it new public IP address.
 How does security group protect your cloud infrastructure? Wrong ans- traffic is allowed to flow betn AWS services but you must add rules to expose ports to public internet. HINT is: A security group with no outbound rules will also block that resources from reaching out to other AWS service endpoints.
