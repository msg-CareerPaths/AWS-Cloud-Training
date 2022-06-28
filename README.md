# Cloud Training: Resources

## Contents

 - [Working Mode](#working-mode)
 - [Environment](#environment)
 - [Docker](#docker)
 - [AWS](#aws)
 - [1. VPC](#1-vpc)
 - [2. EC2](#2-ec2)
 - [3. RDS](#3-rds)
 - [4. S3](#4-s3)
 - [AWS-CDK](#aws-cdk)

## Working Mode

The road-map consists of several steps. In each step, a set of theoretical concepts are explored, supported by reference documentation, book chapters, tutorials and videos. In parallel, a simple application will be built with the learned concepts in the [AWS-CDK](#aws-cdk) chapter.

All the code written must be published on GitHub. Access the [this link](https://classroom.github.com/a/5j3Nt96U) to create your own repository. In order to request a code review from the trainers, you must open a pull request from the develop to the master branch.

## Environment

### Setup Docker

First you need to install Ubuntu on WSL (Windows Subsystem for Linux) following the steps from: 
[https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install)

After installing Ubunt you need to instal Docker without Docker Desktop. You can find the steps needed [here](https://medium.com/geekculture/run-docker-in-windows-10-11-wsl-without-docker-desktop-a2a7eb90556d).

### Setup AWS CLI and AWS CDK
You will need to have [NodeJs](https://nodejs.org/en/) installed and also for developing the CDK App later I would recommend using [VSCode](https://code.visualstudio.com/).

    !!! Important !!!

    Node.js versions 13.0.0 through 13.6.0 are not compatible with the AWS CDK due to compatibility issues with its dependencies.

Install AWS CLI: 

Follow the steps: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html. 

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

-tbd

## AWS

-tbd

## 1. VPC

-tbd

## 2. EC2

-tbd

## 3. RDS

-tbd

## 4. S3

-tbd

## AWS-CDK

-tbd