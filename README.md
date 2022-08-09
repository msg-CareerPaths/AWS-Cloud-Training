# Cloud Training: Resources

## Contents

 - [Working Mode](#working-mode)
 - [Environment](#environment)
 - [Docker](#docker)
 - [AWS Global Infrastructure](#aws-global-infrastructure)
 - [AWS Services](#aws-services)
 - [AWS Management Console](#aws-management-console)
 - [1. VPC](#1-vpc)
 - [2. EC2](#2-ec2)
 - [3. ECS](#3-ecs)
 - [4. RDS](#4-rds)
 - [5. S3](#5-s3)
 - [6. Infrastructure-As-Code](#6-Infrastructure-As-Code)
 - [AWS-CDK](#aws-cdk)

## Working Mode

The road-map consists of several steps. In each step, a set of theoretical concepts are explored, supported by reference documentation, book chapters, tutorials and videos. After the completion of the theoretical part, a small *infrastructure-as-code* application will be built with the learned concepts in the [AWS-CDK](#aws-cdk) chapter.

All the code written in the [AWS-CDK](#aws-cdk) chapter must be published on GitHub. Access the [this link](https://classroom.github.com/a/5j3Nt96U) to create your own repository. In order to request a code review from the trainers, you must open a pull request from the develop to the master branch.

## Environment

### Setup Docker

First you need to install Ubuntu on WSL (Windows Subsystem for Linux) following the steps from: 
[https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install)

After installing Ubuntu you need to install Docker without Docker Desktop. You can find the steps needed [here](https://medium.com/geekculture/run-docker-in-windows-10-11-wsl-without-docker-desktop-a2a7eb90556d).

### Setup AWS CLI and AWS CDK
You will need to have [NodeJs](https://nodejs.org/en/) installed and also for developing the CDK App later I would recommend using [VSCode](https://code.visualstudio.com/).

    !!! Important !!!

    Node.js versions 13.0.0 through 13.6.0 are not compatible with the AWS CDK due to compatibility issues with its dependencies.

Install AWS CLI: 

Follow these steps: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html. 

After installing the AWS CLI run the following command to setup your credentials (for the account used to deploy the final project you'll recive the Access key ID and the Secret Access Key from the account administrator):
```
$ aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: eu-central-1
Default output format [None]: json
```

Install AWS CDK: 

Install the AWS CDK Toolkit globally using the following Node Package Manager command.

    npm install -g aws-cdk

Run the following command to verify correct installation and print the version number of the AWS CDK.

    cdk --version


## Docker

Follow the official docker "Get Started" tutorial [here](https://docs.docker.com/get-started/#start-the-tutorial)

    Ignore "The Docker Dashboard" in the tutorial as it is part of Docker Desktop which requires a license and we are not using it. We will be using Docker on WSL.

Videos with basic Docker tutorials: 
- [https://www.youtube.com/watch?v=d-PPOS-VsC8](https://www.youtube.com/watch?v=d-PPOS-VsC8)
- [https://www.youtube.com/watch?v=WcQ3-M4-jik](https://www.youtube.com/watch?v=WcQ3-M4-jik)

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

## 1. VPC

**VPC** (**V**irtual **P**rivate **C**loud) is the AWS service (and also the name of the resulting resource) that isolates and protects the customer's infrastructure in the AWS Cloud. A VPC (as a resource) is an isolated section of the entire AWS Cloud Network. 

The VPC service provides complete control over the virtual networking environment. Creating a VPC involves defining a range of IPv4 addresses in the form of a CIDR (Classless Inter-Domain Routing) block (e.g. 10.0.0.0/16). The range of IP addresses is further divided into one or more **subnets**. A VPC spans all the AZs in a region, and each subnet is created in a specific AZ.

Each subnet has a **routing table** assigned, which tells instances where to find other IPs. A subnet is considered **public subnet** if its traffic is routed to an Internet Gateway and **private subnet** if it doesn't have a route to the Internet Gateway. An **Internet Gateway** is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the Internet. However, private subnets can access the Internet (if needed) by setting up a **NAT Gateway** (**N**etwork **A**ddress **T**ranslation) and routing the traffic to it.

Lastly, subnets can be configurated with **NACL** (**N**etwork **A**ccess **C**ontrol **L**ists). This additional security level ensures that proper traffic is allowed in and out of one or more subnets. 

Learn more:

- [AWS VPC & Subnets [video]](https://www.youtube.com/watch?v=bGDMeD6kOz0&t=353s)

## 2. EC2

**EC2** (**E**lastic **C**ompute **C**loud) is the AWS service that allows running virtual servers (known as **instances**) in the Cloud.

Launching an EC2 instance involves several configurations:

- Choosing a pre-configured template for the instance

    The pre-configured template is known as **AMI** (**A**mazon **M**achine **I**mages), and it packages the bits needed for the server (including the operating system and additional software). AWS offers several AMIs, but users can also create their own images. 

- Selecting the **instance type** (how big, for what, and, of course, how much)

    Instance types are pre-configured virtual machines. *t2.micro* is an example of an instance type.

- Network configuration. 

    An EC2 instance must be created inside a VPC. Also, a subnet needs to be chosen based on the VPC. The subnet dictates the AZ where the instance will be and whether the instance is public or private. Of course, an EC2 instance can be assigned to a public subnet and have no public IP.

- Setting the storage capacity. 

    AWS provides three options: 
    
    - **Instance Store** - physically attached to the host running the instance, and it is intended only for temporary storage (ephemeral storage);
    - **EBS** (**E**lastic **B**lock **S**tore) - can be seen as an SSD/HDD (or even USB stick) that can be attached to the instance;
    - **EFS** (**E**lastic **F**ile **S**ystem) - can be seen as a network-attached storage.

- **Security Group** configuration.  

    A security group works as a firewall and can be attached to almost any system part. For a component, it specifies what can access (inbound traffic) and to what other components can send data (outbound traffic). Security groups are configured to restrict or allow network access from IP addresses, CIDR blocks, or other security groups.

    A security group blocks by default all inbound traffic (nobody can connect to the component) and allows all outbound traffic (the component can access the Internet). 

    Another essential aspect to remember is that security groups are **stateful**. In this context, stateful means that there is no need to allow traffic for both inbound and outbound specifically. Also, security groups do not have to be confounded with NACL. Security groups control the traffic to/from an instance, and  NACL controls the traffic to/from the network that instance is part of.

    As a remark, security groups were designed to be attached to EC2 instances, but since many services use EC2 under the hood, they can be used across multiple services (e.g. database services).

- other configurations

EC2 service offers two important additional features besides the EC2 instance itself. These are **ASG** (**A**uto **S**caling **G**roup) and **ELB** (**E**lastic **L**oad **B**alancer).

The **Auto Scaling Group** is responsible for managing the EC2s. It must be configured with the desired EC2 instance setup (specified through a **launch template** or **launch configuration**), the number of instance copies, and the scaling mechanism. The rest of the process is automatically handled by ASG, which adds/replaces EC2 instances across AZs, based on needs. The Auto Scaling Group performs **horizontal scaling** for EC2 instances.

The **Elastic Load Balancer** is responsible for distributing the incoming traffic across multiple EC2s. There are four types of Elastic Load Balancer (ELB) on AWS:

- Application Load Balancer (ALB) – suited for load balancing of HTTP and HTTPS traffic;
- Network Load Balancer (NLB) – suited for load balancing of TCP traffic where extreme performance is required;
- Gateway Load Balancer (GLB) – distributes connections to virtual appliances and scales them up or down;
- Classic Load Balancer (CLB) – is old and deprecated.

The **Application Load Balancer** is particularly useful for websites and mobile apps. It has the following components:

- **Load Balancer**

    A load balancer serves as a single point of contact for all end-users.

- **Listener**

    Listeners check for end-user connection requests using the configured protocol and port. 
    
    The **rules** of a listener determine how the load balancer routes requests to its registered targets. Each rule consists of a priority, one or more actions, and one or more conditions. When a rule conditions are met, its actions are performed.

- **Target Group**

    Target group route requests to one or more registered targets (e.g. EC2 instances) using the configured protocol and port. 
    
    Target groups allow configuring **health checks**. These checks are performed on all targets registered to a target group.

The way these components work together is the following. After the **load balancer** receives a request, it evaluates the **listener rules** in priority order to determine which rule to apply. It then selects a target from the **target group** for the rule action.

Learn more:

- [What is Amazon EC2?](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

- [How to Create EC2 Instance in AWS Console [video]](https://www.youtube.com/watch?v=rIi8Pd5Uvbc)

- [EC2 Autoscaling: The Basics and 4 Best Practices](https://spot.io/resources/aws-autoscaling/ec2-autoscaling-the-basics-and-4-best-practices/)

- [AWS - Auto Scaling group with demo [video]](https://www.youtube.com/watch?v=JM1hfA9xBAc)

- [What is an Application Load Balancer? (section 1 and 2)](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)

- [Create an Application Load Balancer (ALB) in AWS [video]](https://www.youtube.com/watch?v=ZGGpEwThhrM)

- [Configuring Auto Scaling Group with ELB Elastic Load Balancer [video]](https://www.youtube.com/watch?v=aOAqH48Cyc8&t=537s)

## 3. ECS

**ECS** (**E**lastic **C**ontainer **S**ervice) is a highly scalable and high-performance container management service in the AWS Cloud. It supports Docker containers and allows to run, stop and manage applications. In simple words, ECS allows the automatic launch of containers (containing the application) in AWS Cloud, starting from a Docker image.

ECS has several components:

- **Task Definition**

    A task definition is a blueprint that describes how a Docker container should launch. It is written in JSON format and contains settings like exposed port, Docker image, CPU shares, memory requirement, the command to run, and environmental variables.

- **Task**

    A task is a running container with the settings defined in the task definition. It can be seen as an instantiation of a task definition. 
    
- **Service**

    A service runs and maintains the desired number of tasks. It is similar to the EC2 Auto-Scaling Group.

- **Cluster**

    A cluster is a logical grouping of services, each composed of one or more tasks. The cluster also groups the resources on which the tasks are running. The cluster resources are either serverless (Amazon Fargate) or managed (Amazon EC2).

- **Container**

    A container is a standardized unit of software development that holds everything that the software application requires to run (code, runtime, system tools, system libraries, etc.). 
    
    Containers are created from a read-only template called **image**. Images are typically built from a Dockerfile. 

- **Container Agent**

    A container agent is a software tool that runs on each container instance in an Amazon ECS cluster. It sends information about currently running tasks, and resource utilization, to Amazon ECS. The container agent can also start and stop tasks when needed.

The way that these components communicate with each other is the following. The Dockerized application is represented by a **task definition** that has a one-to-one relationship with a **service**, which in turn uses it to create many different **task** instances. The service is deployed to a **cluster** of ECS container instances that provide the pool of resources needed to run and scale your application. 

Learn more:

- [Amazon ECS components](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/welcome-features.html)

- [An Overview of AWS Elastic Container Service (ECS) [video]](https://www.youtube.com/watch?v=I9VAMGEjW-Q)

- [How AWS ECS Works a Gentle Introduction [video]](https://www.youtube.com/watch?v=P2gGjvM8liU)

## 4. RDS

**RDS** (**R**elational **D**atabase **S**ervice) is a managed service that makes it easy to set up, operate, and scale a relational database in the AWS Cloud. It supports the following database engines:

- SQL Server;
- Oracle;
- MySQL Server;
- PostgreSQL;
- Aurora (Amazon’s proprietary database);
- MariaDB.

Internally, RDS is just a Relational Database Management System running on an EC2 instance. AWS fully manages it in terms of soft patching, backups, OS maintenance, etc. 

An RDS instance has the following features: 
- automated back-ups
- monitoring
- scalability

    The RDS instance can only be scaled up (compute and storage).

- encryption

    Any RDS instance type can be encrypted at rest.

- DB security groups

    The easiest approach to protect the RDS instance is with a security group that only allows connections from the security group of the application tier.

- read replicas

    They can help with scalability issues for reading operations. The data is asynchronously replicated, so there is a minimal chance of not seeing the latest data. The application must be adapted in order to leverage the read replicas (i.e. connect to a different instance).

- multi-AZ

    The database can run in several AZs at once, and this helps with availability and fault tolerance. The connections are automatically switched to another AZ if one AZ goes down.

- other

Learn more:

- [What is Amazon Relational Database Service (Amazon RDS)?](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

- [AWS RDS MySQL Database Setup | Step by Step Tutorial [video]](https://www.youtube.com/watch?v=Ng_zi11N4_c)

## 5. S3

**S3** (**S**imple **S**torage **S**ervice) is an object storage service in the AWS Cloud. It is designed to store **objects** (e.g. profiles, logs, documents, etc.) in containers called **buckets**. 

A bucket is a globally unique internet container. It has a unique URL and a unique global name. It is recommended that each bucket be used for a single-use case (e.g. one bucket for user files, another bucket for backups, and so on). S3 can store any type of file and provides unlimited storage capacity.

Theoretically, S3 is just a key-value storage system. The key is the complete path to the object, and the value is the object itself. On the same idea, the objects can not be partially changed. The whole object must be replaced if somebody needs a small change.

Uploading/reading files to/from S3 is usually done using the SDK or the REST API (SDK is recommended). All operations work through HTTP(S) requests (e.g. reading a file performs a GET request internally).

Amazon S3 offers additional features for buckets and objects:

- security

    Security can be at the bucket level or at the individual object level. We can configure bucket policies, access point policies, and network access control lists (ACLs). 

- versioning

    Versioning means automatically keeping multiple versions of an object. It prevents accidental deletion.

- tracking

    S3 allows tracking the access to buckets/objects by S3 access logs.

- encryption

    Encryption can be enabled for a bucket.

- replication

    A bucket is created inside a region and is replicated across servers. Optionally, a bucket can be replicated across multiple regions to ensure durability and availability.

Learn more:

- [What is Amazon S3?](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)

- [Getting started with Amazon S3 - Demo [video]](https://www.youtube.com/watch?v=e6w9LwZJFIA)

## 6. Infrastructure-As-Code

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
2. Create a new CDK app on your repository created with GitHub Classroom in the [Working mode](#working-mode) chapter following these steps:
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
   To test the bucket upload a static website and try access the generate URL (could be the website from the frontend training or any other website)