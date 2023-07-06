## Infrastructure-As-Code

A fundamental principle of DevOps is to treat infrastructure the same way developers treat code. Application code has a defined format and syntax. If the code is not written according to the rules of the programming language, applications cannot be created. Code is stored in a version management or source control system that logs a history of code development, changes, and bug fixes. When code is compiled or built into applications, we expect a consistent application to be created, and the build is repeatable and reliable.

Practicing infrastructure as code means applying the same rigor of application code development to infrastructure provisioning. All configurations should be defined in a declarative way and stored in a source control system, the same as application code. Infrastructure provisioning, orchestration, and deployment should also support the use of the infrastructure as code.

Infrastructure was traditionally provisioned using a combination of scripts and manual processes. Sometimes these scripts were stored in version control systems or documented step by step in text files or run-books. Often the person writing the run books is not the same person executing these scripts or following through the run-books. If these scripts or runbooks are not updated frequently, they can potentially become a show-stopper in deployments. This results in the creation of new environments not always being repeatable, reliable, or consistent.

In contrast to the preceding, AWS provides a DevOps-focused way of creating and maintaining infrastructure. Similar to the way software developers write application code, AWS provides services that enable the creation, deployment and maintenance of infrastructure in a programmatic, descriptive, and declarative way. These services provide rigor, clarity, and reliability. The AWS services discussed in this paper are core to a DevOps methodology and form the underpinnings of numerous higher-level AWS DevOps principles and practices.

AWS offers following services to define Infrastructure as a code:
- [AWS CloudFormation](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/aws-cloudformation.html)
- [AWS Cloud Development Kit (CDK)](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/aws-cdk.html)
- AWS Cloud Development Kit for Kubernetes

### AWS-CDK

The AWS Cloud Development Kit (AWS CDK) is an open-source software development framework to define your cloud application resources using familiar programming languages.
Provisioning cloud applications can be a challenging process that requires you to perform manual actions, write custom scripts, maintain templates, or learn domain-specific languages. AWS CDK uses the familiarity and expressive power of programming languages for modeling your applications. It provides high-level components called constructs that preconfigure cloud resources with proven defaults, so you can build cloud applications with ease. AWS CDK provisions your resources in a safe, repeatable manner through AWS CloudFormation. It also allows you to compose and share your own custom constructs incorporating your organization's requirements, helping you expedite new projects.

### Practical steps:
0. Create a new AWS account
1. Follow the CDK Typescript Workshop [here](https://cdkworkshop.com/)
2. Create a new CDK app on your repository following these steps:
   ```
   Reminder: commit and push the code after each step bellow
   ```
   1. Create a new CDK app
   
   2. Create a new stack consisting of a VPC and an EC2 instance on a public subnet. Using the ECS service, run the official nginx image [https://hub.docker.com/_/nginx](https://hub.docker.com/_/nginx)
   ```
   Make sure to choose the free instance type for the EC2: "AWS Free Tier includes 750 hours of Linux and Windows t2.micro instances, ( t3.micro for the regions in which t2.micro is unavailable) each month for one year. To stay within the Free Tier, use only EC2 Micro instances."

   !!! Destroy the stack when not used to avoid costs.
   ```
   3. Add an S3 bucket to the existing stack. Configure the S3 bucket to enable static website hosting and public access.
   To test the bucket, upload a static website and try to access the generated URL (could be the website from the frontend training or any other website).
