DevOps Documentation
 
![Sentia](https://user-images.githubusercontent.com/84912024/127134412-9c7cb214-cca3-43cb-87f6-94a0f99f334c.jpg)

Product Owner: Coen Meulenkamp

Scrummaster: Wessel

Developers: Oualid, Lior, Wessel and Doreen

________________
This documentation presents the process of designing a complete spectrum of a solution and delivering an environment in the public cloud with AWS using Infrastructure as Code. 

1. Assumptions of the architectural decisions made 
________________
1.1 Transformation and Migration to the Public Cloud


To transform and migrate to the cloud, we will first have to make a decision which architectural design will suit the business requirements of the client. We have been researching the AWS Whitepapers of a Multi-tier architecture and the Microservice architecture. Our goal is to design an environment based on serverless and managed services. For now we have selected a Multi-tier architecture pattern as this makes components easy to maintain, decouple and scale. See image below for a simplified version of a three-tier design and a serverless Multi tier design.
  
1.1.1 Requirements Assignments

________________


* (must) be scalable and flexible.
* (must) utilize managed services as much as possible.
* (nice to have) be modernized during this migration in terms of infrastructure technologies used
* Cost Optimization

1.2 Various Components to make up the complete design

________________

Presented below is a high level table of the current On-Premise services used by our client and the assumptions made to either replace or replatform those services in the Public Cloud.  (On-premise architecture) https://nodeployfriday.com/posts/aws-wordpress-reference-architecture/


![Comparison](https://user-images.githubusercontent.com/84912024/129004252-186d5423-12e2-46d7-a6cd-e7ff359437b9.jpg)

Further services we expect to use in our complete design  are EC2 instances, Dynamo database, S3 - Intelligent Tiering storage, a Database Migration Service (DMS), IAM, VPC for a secure connection, Lambda (events), CloudFormation, EFS, Parameters & CloudWatch logs (Please add all along the way)

1.3 In depth research AWS services 
1.3.1 Elastic Beanstalk

________________
To host a web application based on a NodeJS application behind an NGINX reverse proxy we have come to the managed service Elastic Beanstalk.


To get started with Node.js applications on AWS Elastic Beanstalk, all you need is an application source bundle to upload as your first application version and to deploy to an environment. When you create an environment, Elastic Beanstalk allocates all of the AWS resources needed to run a highly scalable web application.


This will then be uploaded to Elastic Beanstalk, and then provide some information about the application. Elastic Beanstalk automatically launches an environment and creates and configures the AWS resources needed to run your code. After your environment is launched, you can then manage your environment and deploy new application versions. The following diagram illustrates the workflow of Elastic Beanstalk.

We have divided the tasks in our group to cover more grounds. We will research several services in the management console, including Lambda, FTP/S3/Quicksight and beanstalk. 


1.3.2 Lambda

________________
Lambda is a service that scales your data automatically.
  

1.3.3 CloudFormation

________________
To deploy our code and set up a formation. We are going to research CloudFormation .AWS CloudFormation gives you an easy way to model a collection of related AWS and third-party resources, provision them quickly and consistently, and manage them throughout their life cycles, by treating infrastructure as code. 


A CloudFormation template describes your desired resources and their dependencies so you can launch and configure them together as a stack. You can use a template to create, update, and delete an entire stack as a single unit, as often as you need to, instead of managing resources individually. You can manage and provision stacks across multiple AWS accounts and AWS Regions. We have decided to go with Cloudformation as this will make it easier to deploy multiple resources. Also this will help with implementing IAC with NodeJS/Yaml

2. The chosen services

________________

One of our customer requirements is to make use of the Kibana dashboard. After careful research through Google, AWS whitepapers and the AWS management console we came to the conclusion that the Kibana dashboard can only be used with ElasticSearch. Since the assignment wants us to use a different service. We have been unable to create a Kibana dashboard. Instead we are looking into alternatives. Several services came up. Such as Quicksight and the Grafana dashboard. Quicksight is cost effective for large scale deployments, as it is pay as you go. Our client will only deploy a small amount of jobs, also Quicksight required all team members to sign in with a free trial. We therefore chose Grafana. Grafana’s user interface is based on version 3 of Kibana, it is a popular open source monitoring tool. We did encounter the complication that Grafana can so far not be used in the availability zone Frankfurt which is our chosen AZ. This can however be fixed with the designated rights. Grafana will be our best option to visualize metrics. 


With not having sufficient time we made the decision not to write any code in SDK or Terraform. We used the managed service CloudFormation. This did require us to become more experienced in YAML. CloudFormation overal gives us the perfect tool to deploy multiple services in the cloud, and it works seamlessly with all services we like to use to satisfy the clients need. 


Since we needed to replatform the cron server to the public cloud with a small amount of jobs that needed to be executed. The serverless service Lambda is the first that came to the mind of the developers. Lambda can effortlessly scale up and down, can be used for a short time frame and will interact with CloudFormation.  


One of the first and easiest choices the team decided on, was using AWS S3 as our service for storing data. A very versatile service with amazing and intelligent components. Such as intelligent- tiering and versioning of a bucket to prevent accidental deletion of an object. Upon creation, server access logs, API logs, tags and encryption can be set up  to secure and personalise the service. 


Another win we encountered with S3, is that it will function as a back-up for EFS, this will be our replacement service in the cloud for the FTP server. There are multiple ways to host a FTP server. Earlier we described the usage of AWS Transfer Family or using EC2 instances. The combination of EFS with S3 as back-up is more cost effective. EFS retains data after EC2 instance termination, it is furthermore easy scalable, serverless and Lambda compatible. 


2.1 Learnings & Take - Away

________________

We dealt with not having the sufficient knowledge to make a good start on the project. This resulted in the time taken to do research. We spent about a week and half on doing so, with the complete project time-frame taking 3 weeks in total. On several days we did not have a complete team, there was however always a plan made to further divide tasks for the rest of the day.  


What we definitely can take away from this project is that research is never wasted. We did learn a lot about the several managed and serverless services AWS has to offer in dept. We made a start with S3, Cloudformation, Beanstalk, Lambda, documenting our progress, and working with Github. 


Meetings with the product owner, more hands-on experience, planning, knowledge and a longer timeframe will be beneficial before tackling a new project of the same size. 

3. Deliverables
________________
1. An architectural design for all the components and all the environments.
2. An IaC project for deploying an MVP demo (excluding the CRON and the ElasticSearch requirements).
   * for AWS, write your IaC using: AWS CDK (preferred), or alternatively with AWS CloudFormation.
   * for Azure, write your IaC using: Bicep (preferred), or alternatively with ARM Templates.
3. Include a simple time log of the activities you have performed.
4. Document any assumptions and decisions you have made.
5. A GIT repo with all the above.
 

4. Architectural design
________________

5. IAC Project for deploying an MVP demo
________________

https://github.com/WesselSoepboer/DevOps_Sentia/blob/main/Sentiacloud.2
________________




















  
