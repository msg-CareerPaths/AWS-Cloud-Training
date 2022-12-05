## AWS Global Infrastructure

**AWS** (**A**mazon **W**eb **S**ervices) is a cloud computing platform that offers tools and solutions for enterprises or software developers. Going deeper into its infrastructure, AWS actually consists of several independent clouds running in different regions around the world. 

An **AWS Region** is a physical location for AWS data centers. *Ireland (eu-west-1)* is an example. Each region has an independent infrastructure, independent services (some regions get new features sooner than others), and independent pricing. The motivation of multiple regions is that if there were just one, then end-users from all around the world would have to connect to it. This situation leads to high latency and bottlenecks. Moreover, if a natural disaster would destroy the data centers in that region, no insurance would be able to cover all the business disruptions.

Additionally, each region consists of several **Availability Zones (AZs)**. AZs consist of one or more discrete data centers, each with redundant power, networking, and connectivity. An availability zone is isolated, but the availability zones in a region are connected through low-latency links. When you run a service, you often run it in a specific availability zone. An example of AZ is *eu-west-1**a***.

There are also data centers outside AWS regions and availability zones. These locations are called **edge locations** and are designed to deliver content to the end-users with the lowest latency possible. They are often located in major cities, being closer to end-users than regions or availability zones.

Learn more:

- [AWS Global Cloud Infrastructure [video]](https://www.youtube.com/watch?v=RPis5mbM8c8)
