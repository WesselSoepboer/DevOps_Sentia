####Customer product demands and current information about the customer on premise infrastructure

Currently in use:

1.Currently hosting a customer facing web application based on a NodeJS application behind an NGINX reverse proxy

2.Using a MongoDB cluster for storing data. 

3.An FTP server for document storage

1. Maintain a cron server, mostly Bash and Python scripts, relevant to a small amount of jobs that need to be executed a few timer per day(no more than once per hour).
2. All above services are hosted on severak virtual machines.
3. The customer has 3 environments:
    1. Test
    2. Acceptance 
    3. Production
    
Dev-ops Deliverables

1.An architectural design for all the components and all the environments

2.An IaC project for deploying an MVP demo (excluding the CRON and the Elasticsearch requirements).

For AWS, write your IaC using: AWS CDK (Preferrred), or alternatively with AWS CloudFormation.

3.Include a simple time log of the activities you have performed.

4.Document any assumptions and decisions you have made.

1. A GIT repo with all the above.

- Time frame: 12 months.
- All application and infrastructure logs must be exported to an Elasticsearch Cluster.
- The customer needs to have access to the Kibana dashboard within their HQ. But the cluster/dashboard should not be publicly accessible.
- Cost optimization should be applied when necessary, even if a few application related modifications are necessary.
- Environment isolation is important, but some shared services would be acceptable if the result in major cost reduction.
- Must be scalable and flexible.
- Must be utilize managed services as much as possible.
- (Nice to have)Be modernized during this migration in terms of infrastructure technologies used.
