## IAM

**IAM** (**I**dentity and **A**ccess **M**anagement) is the web service that securely controls the access to AWS resources. IAM defines **who** can perform actions in the AWS account (authentication) and **who** has access to **what** resource (authorization).

IAM identities:

- **Users** 

    There are two types of users:

    - root user
        
        This user is generated when you first create an AWS account. It is used to close the account, change the account email address, or modify the support plan.

    - individual users
    
        These users are persons or applications needing to access AWS resources. They can perform administrative tasks, access application code, configurations, etc.
    
    IAM users can be used both for signing in to the AWS Console and for programmatic sign-in to the AWS CLI or AWS API. The programmatic sign-in requests some special credentials called **access keys**.

    Access keys consist of two parts: an access key ID (for example, AKIAIOSFODNN7EXAMPLE) and a secret access key (for example, wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY). These are like a user name and password and they must be used together to authenticate the requests. 

- **Groups**

    Groups are a collection of IAM users. It is used to apply common access controls to all members. The access is controlled through policies and roles. Examples of possible IAM groups are _developers group_ or _project managers group_.

- **Roles**

    Roles are similar to IAM users and allows defining policies for accessing the AWS resources and services. The differences between roles and users are:

    - a role does not have any credentials (password or access keys)
    - a role can be assumed by any IAM user when needed (for example, a user needs temporary  permissions to perform a specific task)
    - a role can not belong to a group
    - a role can be associated with AWS resources (for example, an EC2 instance can have a role attached to be able to access other resources such as S3 buckets, RDS database etc.)

- **Policies**

    Policies are documents that manage permissions for users, groups, and roles. Most policies are stored in AWS as JSON documents. All permissions are implicitly denied, and the most restrictive policy is applied.

    A policy document contains the following:

    - Version - e.g. *2012-10-17*
    - Id (optional) - an identifier for the policy, e.g. *S3-Account-Permissions*
    - Statement - one or more individual statements
        
        Statements consist of: 
        
        - Sid (optional) - an identifier for the statement, e.g. *1*
        - Effect - whether the statement allows or denies access (*Allow* or *Deny*)
        - Principal (required in only some circumstances) - the account/user/role to which this policy applied to, e.g. *arn:aws:iam:123456789012:root* (root user)
        - Action - a list of actions this policy allows or denies, e.g. *s3:GetObject* (allows reading S3 bucket objects) or *s3:PutObject* (allows adding objects in S3 bucket) 
        - Resource (required in only some circumstances) - a list of resources to which the actions applies to, e.g. *arn:aws:s3:::my-bucket/* *
        - Condition (optional) - conditions for when this policy is in effect, e.g. *aws:MultiFactorAuthPresent: true*

    AWS has several managed policies that cover most of the cases when you need a policy. However, you can write your own policy for your specific use case.

    Policies can also appear in other circumstances, not only as policies assigned to IAM identities (known as **Identity-based policy**). Another important type of policy is **Resource-based policy**. The most common examples of resource-based policies are Amazon S3 bucket policies that grant permissions to the principal that is specified in the policy. 

Learn more:

- [IAM Identities (users, user groups, and roles)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html)
- [Policies and permissions in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)
- [AWS IAM Core Concepts You NEED to Know [video]](https://www.youtube.com/watch?v=_ZCTvmaPgao)
