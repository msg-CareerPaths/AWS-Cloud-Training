## VPC

**VPC** (**V**irtual **P**rivate **C**loud) is the AWS service (and also the name of the resulting resource) that isolates and protects the customer's infrastructure in the AWS Cloud. A VPC (as a resource) is an isolated section of the entire AWS Cloud Network. 

The VPC service provides complete control over the virtual networking environment. Creating a VPC involves defining a range of IPv4 addresses in the form of a CIDR (Classless Inter-Domain Routing) block (e.g. 10.0.0.0/16). The range of IP addresses is further divided into one or more **subnets**. A VPC spans all the AZs in a region, and each subnet is created in a specific AZ.

Each subnet has a **routing table** assigned, which tells instances where to find other IPs. A subnet is considered **public subnet** if its traffic is routed to an Internet Gateway and **private subnet** if it doesn't have a route to the Internet Gateway. An **Internet Gateway** is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the Internet. However, private subnets can access the Internet (if needed) by setting up a **NAT Gateway** (**N**etwork **A**ddress **T**ranslation) and routing the traffic to it.

Lastly, subnets can be configurated with **NACL** (**N**etwork **A**ccess **C**ontrol **L**ists). This additional security level ensures that proper traffic is allowed in and out of one or more subnets. 

Learn more:

- [AWS VPC & Subnets [video]](https://www.youtube.com/watch?v=bGDMeD6kOz0&t=353s)
