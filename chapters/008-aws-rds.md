## RDS

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
