## Working Mode

The road-map consists of several steps. In each step, a set of theoretical concepts are explored, supported by reference documentation, book chapters, tutorials and videos. After the completion of the theoretical part, a small *infrastructure-as-code* application will be built with the learned concepts in the [Infrastructure-As-Code](https://github.com/msg-CareerPaths/aws-cloud-training/blob/main/chapters/009-infrastructure-as-code.md) chapter.

All the code written in the [Infrastructure-As-Code](https://github.com/msg-CareerPaths/aws-cloud-training/blob/main/chapters/009-infrastructure-as-code.md) chapter must be published on GitHub. Create your own repository. In order to request a code review from the trainers, you must open a pull request from the develop to the master branch.

## Environment

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
