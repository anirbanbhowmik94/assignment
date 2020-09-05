# Assignment
### To build Application Image :
```
cd submission
docker build -t assignmentapp .
```
### To start all services - Application, Redis & Kafka :
```
cd submission
docker-compose updocker-compose up -d
```
### To deploy Application in ECS :
```
cd submission
aws cloudformation create-stack --template-body file://$PWD/infra/app.yml --stack-name app-cluster
```
**The CloudFormation Template assumes that a parent Network Stack has been created in AWS Fargate (as per the Assignment.md Expectations Section) and the following are exported :**
* ClusterName (The name of the ECS cluster)
* VPCId (The ID of the VPC in which thestack is deployed)
* SubnetOne (Public subnet one)
* SubnetTwo (Public subnet two)
* ContainerSecurityGroup (A security group used to allow containers to receive traffic)
* PublicListener (The ARN of the public load balancer's Listener)
* ECSTaskExecutionRole (The ARN of the ECS role)
* DomainName (Domain Name of Load Balancer)
