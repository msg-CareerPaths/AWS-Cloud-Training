## ECS

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
