## EC2

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
