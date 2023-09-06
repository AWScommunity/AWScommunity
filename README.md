Listed on base of priority  [.](https://gist.github.com/AWScommunity/33ab6119dcdeffa149f245f3257fd889#comments)

aws..com bibek...@g 3..3     (aws.amazon.com sh..@g 37W..337W..3 DOESNT work now)

[AMAZON account for registering aws cloud architect exams](https://aws.amazon.com/certification/certification-prep/testing/) etc   

and [also for learning cloud practitioner FREE ENROLL in aws skillbuilder](https://explore.skillbuilder.aws/learn/course/12483/play/50113/aws-certified-cloud-practitioner-official-practice-question-set-clf-c01-english) is with shrsmriti@g r.T.1 or 2- Iforgot
- https://console.aws.amazon.com/billing/  ma jau ra di ko card rakha default ma ani yei lai primary set gara ani balla hunx pay succes

![236808475-0e7cda80-2f1d-43f5-aba2-9d98579b3e68](https://github.com/AWScommunity/AWScommunity/assets/109033173/944202c3-8f99-4c53-8d75-2186bf8ad1a2)

---
**C L O U D . P R A C T I T I O N E R - code: CLF- CO1 **

**1.CLOUD CONCEPT (IknowIt) - 26% marks**

1.1 WHY cloud? Agility,Elasticity, Flexibility & Security

1.2 TCO 

1.3 AWS Pricing Model

1.4 [Cost explorer](https://www.youtube.com/watch?v=oE8TNKGmc40) & [Trusted Advisor](https://www.youtube.com/watch?v=HIR6z0Fr1Yo)

**2. SECURITY & COMPLIANCE - 25%**

2.1 HIPAA Compliance:
HIPAA forces us to encrypt-decrypt-data-by-using-PEM-files-or-etc Post:
So anyway as I was saying about HIPAA compliance, Health.Insurance.Protocol.sthg is law passed by US govt about how health data and other must follow Business.Associate.Agreement BAA , how it's in transit data. Ie data when passing thru servers like we do in API passing betn different servers say from db to say app servers like GraphQL operates w, should all be encrypted eg. TLS, xyz encrypted as verified by AWS.Certificate.Manager ; moreover there's Cloudtrail etc to watch who has had access to data so that we can submit it to data security audit when they ask for..
So, this std tho was pioneered on health data I think has been extended to all other sectors like say finance industry, payment gateway industry.
     So, AWS tools are HIPAA eligible means they can be and so have to be worked to make HIPAA compliant. They are not HIPAA compliant on their own. That's where is also: shared responsibility comes in.

```
Also, aws Security compliance program also do Risk Mgmt: Follow following stds ie COBIT, AICPA, NIST.
{COntrol.OBjectives.for.Information&relatedTechnologies. not an information safety framework like data encrypt decrypt etc. about the control and safety of sensitive information and provide a reference framework.}   {American Institute of Certified Public Accountants in US (AICPA) who created the Service Organizational Controls (SOC) standard.    Through the SOC 2 standard, AICPA created guidelines to be used by a certified accounting firm to audit, assess, and attest to a company’s compliance and security practices. Security, availability, confidentiality, processing integrity, and privacy are Trust Service Criteria (TSC) developed by AICPA in order to help companies set criteria for managing customer data. }   { National Institute of Standards and Technology is a non-regulatory government agency that develops technology, metrics, and standards to drive innovation and economic competitiveness at U.S.-based organizations in the science and technology industry. As part of this effort, NIST produces standards and guidelines to help federal agencies meet the requirements of the Federal Information Security Management Act (FISMA). NIST also assists those agencies in protecting their information and information systems through cost-effective programs.}       and aws security pgm also constantly scans service endpts for vulnerabilities
```

2.2 Identity.Access.Management and User&Groups

![IAM](https://user-images.githubusercontent.com/109033173/223469280-8bb02ecb-ebdd-4ab9-a842-aef5c11cb3eb.png)

IAM is about needs to deal w administrating diff accounts as dgm. so as in famous yt v in amazon web services channel. 
For eg, if u want s3 to be accessed by say dev account ID345, then simply write s3accessPolicy: true yml for ID345 in that principal aka master aka root aws acc. 

```
IAM

> handles authentication (who can), authori(what they can)
> users can have programmatic access n/or console access
> best practices
   . delete root acc keys    .Instead use IAM acc       .Use groups   .use roles   
   .rotate credentials: Symmetric key is where u use same key for encrypting n decrypting as well. Symm key is used default by AWS and symm keys eg are .. whereas asymm key is when u use one key to encrypt n     another to decrypt. Asymm key are Elliptic curve technology, RSA etc.

     Anyway Key rotation is needed becoz security compliance audit demands u change keys to instances once every mo. or more frequently
 but if u are lazy bear, just changing key once a while, then there's one click gui button change to rotate key pair once every yr n u don't have to do manually. 
So key pair is just, like u got 3 doors , n u rotate key door combination shifted from door a to b to c to a once while .
  
   .remove unneccess users
  
```
![image](https://user-images.githubusercontent.com/109033173/236812602-273c3f0e-db0e-43c6-b52e-40cabae54288.png)

![image](https://user-images.githubusercontent.com/109033173/221377563-d45c01af-6fd0-483d-9611-e8ea931090b3.png)

2.3 MFA

![Untitled](https://user-images.githubusercontent.com/109033173/221377586-ea23b004-47ff-4de7-81cd-d9fb42aa02c3.png)

achieve single sign-on in principal aka root aws acc by configuring SAML2.0

Now lets get around some tricky situation below where for SSO, SAML2.0 is not configured.

``` 
suppose some X company has employees who need to run internal applications that access company's aws resources. these employees already have user credentials in company's Identity Auth system, WHICH DOESNT SUPPORT SAML2.0 ,and company doesnt want to create seperate IAM user for each company employees.
    SO, IN THIS CASE, SSO setup can be designed by:
 creating custom identity broker application which authenticates employees using existing system, and 
a) uses GetFederationToken API call and passes permission policy to gain temporary access credentials from Security.Token.Service.
b) uses AssumeRole API call to gain temporary role based access to AWS
```

btw: Federation unlike SSO or unlike authentication is a collection of domains that have established trust. The level of trust may vary, but typically includes authentication and almost always includes authorization. A typical federation might include a number of organizations that have established trust for shared access to a set of resources.
also dyk that while doing IAM in root, you have to grant or deny permissions to individual IAM, or in group ,or do to federated domains.
    
and if we want 50 new employees to have access to S3 buckets with unltd previlege and rest 60 with not, then I simply do: 
create new group adding that 50 and add S3 bucket policy with unltd previlege.

If u want details 1 feet below view of how it works, then go >>
https://user-images.githubusercontent.com/109033173/192111690-0812fa89-41e8-447d-81d8-de7e122c28dc.png

2.4 NACL Network.Access.Control.List

2.5 CloudWatch: naam batai spasta chh, ahile kun compute wa user le kati kati resource khai raach

2.5 CloudTrail: naam batai spasta chh, kun compute le kati resource khayo . ie. Log files

**3 TECHNOLOGY- 33%** 

3.0 Elastic BeanStalk : It handles the auto- provisioning of the infrastructure, deploys the application, handles the load by applying auto scaling, and monitors the application.                             to create artifacts of codes like .jar .exe (novice me thinks- artifact creation is next natural compulsion in case of some s/w, apps but not so, if we are doing some https websites only BUT idk if i am right). then comes writing the sequence of what we did in Lpost2 and creating artifacts, all in one aws pipeline so that it knows what next to do on its own. I've summarized it below, open in new tab: https://giphy.com/embed/2wLc0VnNbFwyRCZn2U

3.1 CloudFormation : It provides template while creating resources. someway slightly like html templates

3.2 [Opswork](https://www.youtube.com/watch?v=BhNfhHXvhhc)

3.3 [CodeCommit](https://www.youtube.com/watch?v=46PRLMW8otg)

---
3.4 EC2 - IknowIt

ec2 reserved instances  

ec2 spot instances works on the spot means borrowing unused ec2s if needed       

ec2 dedicated instance -Spot instances allow u to bid on unused Amazon EC2 capacity n pay by hr. Dedicated Spot instances have the same price as standard Spot instances. WHEREAS Dedicated Reserved Instances provide a capacity reservation so that you can have confidence in your ability to launch the number of instances you have reserved when you need them. Dedicated Reserved Instances also provide you with a significant discount (up to 75%) compared to On-Demand instance pricing.

ec2 lightsail - sab kura paila ready-ed xa jastai networking etc all needed

ec2 dedicated hosts are usually when company wants to migrate n tier web applications to AWS and company wnats to control placement of instances and have visibility to underlying sockets and cores for listening purposes.

ecs ec2 good when u want more control of deployed infrastructure, ecs fargate good when u want to have less mgmt overhead. 

Also, ecs agent is to start stop ecs container instance whereas Task Definition describes container n volume defn of ecs task.

---

```
When using AWS for R&D ahead of planned migration, how do you prevent unexpected increases or spikes in billing?
1.  Using Root AWS acc, enable billing alerts in user preferences. Then use CloudWatch to create billing alarm & set threashold to specific dollar amount for your est monthly charges.  (correct ans)

2.  Using Root AWS acc, activate IAM access to billing information for account. 
Ensure your IAM user have BillingFullAccess Group Policy. Then from billing dashboard, check accrued charge once a day.

3.  Use bill dashboard to create cost budget. Input max amount you want to be charged each mo. 
Any charges that occur over this amount will cause AWS to auto suspend these resources.

4.  If you are using AWS free tier, you will have to confirm usage of any service that goes over AWS free tier limits.
```

3.5 S3
![s3](https://user-images.githubusercontent.com/109033173/221375145-c9aade21-8a6e-49a0-bc4f-1182c6367f9e.png)

![image](https://user-images.githubusercontent.com/109033173/235315187-a3b14b00-b597-415e-9b61-2b6e7e6990c0.png)
 
3.6 AZs & Regions, EdgeLocations
![image](https://user-images.githubusercontent.com/109033173/221374914-ebf2c34c-6aa6-48b4-ab75-34781cb882c7.png)

3.7 SQS
![SQS](https://user-images.githubusercontent.com/109033173/221375039-1f4ef01e-db1c-44fe-a977-944991c8f3b2.png)

3.8 SNS , ELB, VPC(<- look my white note)
3.9 EBS,  Route53

**4 BILLING & PRICING - 16%**

On Demand Pricing, Dedicated Host, Spot Instances, Billing Alert and Budget,
Billing Support

---
![image](https://user-images.githubusercontent.com/109033173/185744444-ed1e7198-e582-4199-b1a2-a7dc6970eae6.png)

---
![image](https://user-images.githubusercontent.com/109033173/193422322-b40f7d08-68b7-4d6f-8a3e-faaf23aa1606.png)

![image](https://user-images.githubusercontent.com/109033173/192141241-258f9499-d4de-42c7-9b13-fe79d3c043b3.png)

---
![image](https://user-images.githubusercontent.com/109033173/180044421-2a5284ba-5783-4e38-a19c-130fa906bf25.png) 
---
![CLF- exam](https://user-images.githubusercontent.com/109033173/223468690-82307b7a-97eb-42e1-879b-9aa7fad55a36.png)

