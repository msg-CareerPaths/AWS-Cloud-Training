## AWS Global Infrastructure

**AWS** (**A**mazon **W**eb **S**ervices) is a cloud computing platform that offers tools and solutions for enterprises or software developers. Going deeper into its infrastructure, AWS actually consists of several independent clouds running in different regions around the world. 

An **AWS Region** is a physical location for AWS data centers. *Ireland (eu-west-1)* is an example. Each region has an independent infrastructure, independent services (some regions get new features sooner than others), and independent pricing. The motivation of multiple regions is that if there were just one, then end-users from all around the world would have to connect to it. This situation leads to high latency and bottlenecks. Moreover, if a natural disaster would destroy the data centers in that region, no insurance would be able to cover all the business disruptions.

Additionally, each region consists of several **Availability Zones (AZs)**. AZs consist of one or more discrete data centers, each with redundant power, networking, and connectivity. An availability zone is isolated, but the availability zones in a region are connected through low-latency links. When you run a service, you often run it in a specific availability zone. An example of AZ is *eu-west-1**a***.

There are also data centers outside AWS regions and availability zones. These locations are called **edge locations** and are designed to deliver content to the end-users with the lowest latency possible. They are often located in major cities, being closer to end-users than regions or availability zones.

Learn more:

- [AWS Global Cloud Infrastructure [video]](https://www.youtube.com/watch?v=RPis5mbM8c8)

## AWS Services

AWS offers over 200 services, configurable according to user needs. These services are grouped into several categories, as follows:

- **Compute**: provides tools to develop, deploy, run, and scale applications in the AWS Cloud (e.g. EC2, Lambda, etc.);
- **Containers**: offers services that securely store and manage container images (e.g. ECS, EKS, etc.);
- **Database**: supports all database needs like relational, NoSQL, in-memory, or graph databases (e.g. RDS, DynamoDB, etc.);
- **Developer Tools**: offers services to accelerate the software development process and release cycle (e.g., CodeCommit, CodePipeline, etc.);
- **Management Tools**: includes tools for lifecycle management—control, environment security, operational efficiency (e.g. CloudWatch, System Manager, etc.);
- **Networking and Content Delivery**: offers solutions for running applications with the highest level of reliability, security, and performance in the AWS Cloud (e.g. VPC, CloudFront, etc.);
- **Security, Identity, and Compliance**: provides tools to achieve compliance and to protect the infrastructure and data from threats and exposures (e.g. IAM, Secrets Manager, etc.);
- **Storage**: offers solutions for storing the data in the AWS Cloud (e.g. S3, EBS, etc.);
- other categories (Analytics, Application Integration, Cost Management, End User Computing, Game Tech, Internet of Things, Machine Learning, Media Services, Migration and Transfer, etc.);

This chapter covers the most popular five services from the category of networking, compute, container, database, and storage, respectively. Each of these services plays an important role in establishing a robust infrastructure.

## AWS Management Console

The AWS Management Console is a web application that comprises a broad collection of service consoles for managing AWS resources. When you first sign in, you see the Console Home page. The home page provides access to each service console and offers a single place to access the information you need to perform your AWS related tasks.

Learn more:

- [Getting Started with the AWS Management Console](https://aws.amazon.com/getting-started/hands-on/getting-started-with-aws-management-console/?pg=gs&sec=gtkaws)
