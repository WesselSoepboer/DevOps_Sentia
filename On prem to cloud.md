***On prem to cloud service conversion

1. Currently hosting a customer facing web application based on a NodeJS application behind an NGINX reverse proxy
    1. Host the code on an ec2 instance
    2. Elastic beanstalk  around the ec2 instance for easy deployment elastic load balancing, auto scaling and security groups.
    3. Link: 

        [https://dev.to/shadid12/how-to-deploy-your-node-js-app-on-aws-with-nginx-and-ssl-3p5l](https://dev.to/shadid12/how-to-deploy-your-node-js-app-on-aws-with-nginx-and-ssl-3p5l)

        [Deploy a Node.js Application on AWS EC2 with Nginx as a Reverse Proxy](https://medium.com/@ramavathvinayak/deploy-a-node-js-application-on-aws-ec2-with-nginx-as-a-reverse-proxy-e8f41f1edaef)

Currently in use:

1. Using a MongoDB cluster for storing data. 
    1. option one is to do use mongoDB in AWS
        1. Use AWS Cloudformation
        2. Link:

            [https://docs.aws.amazon.com/quickstart/latest/mongodb/architecture.html](https://docs.aws.amazon.com/quickstart/latest/mongodb/architecture.html)

    2. Use Amazon DocumentDB
        1. Link: [https://aws.amazon.com/getting-started/hands-on/move-to-managed/migrate-mongodb-to-documentdb/](https://aws.amazon.com/getting-started/hands-on/move-to-managed/migrate-mongodb-to-documentdb/)

2. An FTP server for document storage
    1. (Use amazon transfer family naar een) S3 is managed
3. Maintain a cron server, mostly Bash and Python scripts, relevant to a small amount of jobs that need to be executed a few timer per day(no more than once per hour).
    1. AWs Lambda?
    2. Amazon CloudWatch(CloudWatch events
    3. Amazon ECS using Amazon EventBridge
4. All above services are hosted on several virtual machines.
    1. EC2 Instances
    2. What type of instance?
5. The customer has 3 environments:
    1. Test
    2. Acceptance 
    3. Production

    Kan met zo te zien met Elastic beanstalk of met AWS Device Farm

Dev-ops Deliverables

1.An architectural design for all the components and all the environments

2.An IaC project for deploying an MVP demo (excluding the CRON and the Elasticsearch requirements).

For AWS, write your IaC using: AWS CDK (Preferrred), or alternatively with AWS CloudFormation.

3.Include a simple time log of the activities you have performed.

4.Document any assumptions and decisions you have made.

1. A GIT repo with all the above.

- Time: 12 months.
- All application and infrastructure logs must be exported to an Elasticsearch Cluster.
- The customer needs to have access to the Kibana dashboard within their HQ. But the cluster/dashboard should not be publicly accessible. \
    - Grafana instead of kibana, quicksight might be possible aswell
- Cost optimization should be applied when necessary, even if a few application related modifications are necessary.
- Environment isolation is important, but some shared services would be acceptable if the result in major cost reduction.
- Must be scalable and flexible.
- Must be utilize managed services as much as possible.
- (Nice to have)Be modernized during this migration in terms of infrastructure technologies used.

Notes van Coen

NGIX reverse proxy = elastic load balancer

MongoDB = DynamoDB / DocumentDB

NodeJS applicatie = Fargate ECS container

Document storage = S3

Cron server = cloudwatch Events/eventbridge timed events |→ Lambda functies.

Herbruiken van code en het parametrizeren van Tags.

Environment Tag. VPCs in accounts

DynamoDB Cluster Logs

|→ Cloudwatch → DynamoDB

Quicksight met athena DynamoDB Connector 
VPN

Allemaal in een private subnet zonder internet gateway route
