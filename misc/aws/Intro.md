# Intro

## AWS in Distributed Systems

| Feature | How it helps in DS |
| --- | --- |
| Global Regions and AZs | Deploy parts of your system across data centres and continents for redunancy, fault tolerance, latency control |
| Scalable Compute (EC2, Lambda, ECS) | Scale horizonatally |
| Storage Systems (S3, EFS, DynamoDB) | Highly available and eventually consistent storage |
| Messaging (SQS, SNS, EventBridge, Kafka/MSK) | Enable async comm and decoupled services |
| Load balancing + auto scaling | dynamically distribute traffic and scale nodes in/out |
| Managed DBs (RDS, Aurora, DynamoDB) | Offer replication, sharding, consistensu modes |
| CloudWatch and X Ray | Observability for monitoring distributed traces, logs, and metrics |

## Common Archiectures

- Microservices using lambda + api gateway
- event driven systems using SQS, SNS, DynamoDB streams
- Global databases with DynamoDB Global Tables or Aurora Global DB
- Big Data piplines using Kinesis, EMR, S3
- CQRS / Event sourcing systems with lamba and dynamodb

## Example - Fault tolerant order processing system

- API → API Gateway + Lambda
- Orders → DynamoDB
- Processing → SQS queue + consumer lambda
- Notifications → SNS
- Files → S3