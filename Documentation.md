### Documentation of the descisions and assumptions made for DevOps_sentia

DevOps Documentation

Product Owner: Coen Meulenkamp
Scrummaster:
Developers: Oualid, Lior, Wessel and Doreen

Assignment
Presentation 
DevOps Sheets for Graphs/Tables
Diagram.IO
Kibana
Github Repo
Architecture

To migrate from on premise to the public cloud we will be using AWS as our cloud provider

We will also follow along with the  5 migration steps: 
Planning and Assessment
Migration Tools
AWS Cloud Storage
Migration Strategies
Application Migration Options


Tools
Google Docs
Google Slides
Kibana Dashboard
AWS Management Console 
Jira
Github
Slack
Zoom

Assumptions
Since we will be moving forward from On premise to the cloud, we are thinking of several tools to use, and trying to implement managed services. We will be using the following:
EC2
DynamoDB
S3 - Intelligent Tiering 
Database Migration Service (DMS) 
IAM
VPC 
Lambda
CloudFormation 
EFS
Parameters
CloudWatch logs
ElasticSearch Service

The current On Premise environment of Sentia Recruitment vs the managed services we would like to use in AWS 

On Premise
Public Cloud
NodeJS app
Elastic Beanstalk
NGINX reverse proxy
Lightsail
FTP Server
EFS
Cron Server
Lambda
MongoDB
DynamoDB/S3
Kibana Dashboard
ElasticSearch Service

Requirements
(must) be scalable and flexible.
(must) utilize managed services as much as possible.
(nice to have) be modernized during this migration in terms of infrastructure technologies used
Cost Optimization

Assignment
The main assignment is to transform and migrate the 3 environments to the Public Cloud. These consist of Test, Acceptance and Production

Tomorrow

Update Wessel 
Github account 
Kibana gebeuren (Elasticsearch service) 
Inplannen (Jira/Poker) 
Een start maken met de Architectuur 

Deliverables
Please provide the following:
An architectural design for all the components and all the environments.
An IaC project for deploying an MVP demo (excluding the CRON and the ElasticSearch requirements).
for AWS, write your IaC using: AWS CDK (preferred), or alternatively with AWS CloudFormation.
for Azure, write your IaC using: Bicep (preferred), or alternatively with ARM Templates.
Include a simple time log of the activities you have performed.
Document any assumptions and decisions you have made.
A GIT repo with all the above.
