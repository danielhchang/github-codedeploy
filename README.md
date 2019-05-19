# [AWS Code Deploy](https://docs.aws.amazon.com/codedeploy/index.html) Notes

======

## My study path

* Read the FAQ
* Try the tutorial
* [AWS CodeDeploy Udemy Course](https://www.udemy.com/aws-codedeploy/)

## Terminology/Glossary

Application: The first entity you'll create in CodeDeploy is an Application.  Within CodeDeploy, you'll identify the **Instances** running the **Application**, create **Revisions** (a collection of code, configuration files, executables, packages, scripts, etc.) and **Deployment Groups** (collection of the **Instances**)

Revision: This is a specific version of deployable content.  Collectively, the appspec.yml, and files in the files and scripts folder are grouped together in a Revision.  Each revision has one and only one appspec.yml.  

Deployment Group: the set of instances targetted for deployment.

Deployment Configuration: How deployment will proceed.  Can be OneAtATime, AllAtOnce, etc.  There's a default configuration is OneAtATime.

## My notes

CodeDeploy is used to automate code deployments.  It can be used to deploy your application to instances running either on-premise or within AWS.  On AWS, it supports ec2, ecs, and lambda.  For ec2/on-premise, there are both Linux and Windows agents.

The udemy course appears to be pretty dated and I struggled to find the right ami I could use to run the supplied CloudFormation Template.  I did learn that the Amazon Linux 2 did not have all the needed packages and so the CodeDeploy demos didn't work.  Replacing this with the Amazon Linux AMI worked.  It's likely that the "broken" Linux AMI didn't have ruby pre-installed.  Also note that AMIs are region specific.

When creating revisions, the basic directory structure is
.
├── appspec.yml
├── files
└── scripts

Within the files directory, you'll place all the files that you'll be copying to the target servers.  These are the source files (such as text and binary files, executables, packages, and so on).  

With the scripts directory, you'll have all the scripts needed for your lifecycle event hooks, for instance the scripts needed to be run BeforeInstall, AfterInstall, ApplicationStart, ApplicationStop and so on.  
