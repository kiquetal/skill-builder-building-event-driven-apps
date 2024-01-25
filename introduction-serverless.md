### Introduction to Serverless

Serverles technologies eliminate infraestructure management tasks like capacity provisioning and patching,
so you can foucs on writing code that serves your customers. These techonologies feature automatic scaling, built in 
high availability and pay-for-use billing model to increase agility and optimize costs.

- No server management
- Pay for value
- Flexible scaling
- High availability

Step functions is a workflow orchestration service,
- Buil-in service primitives


- AWS service integrations


- Built-in error handling

Lambda.ServiceException
Lambda.AWSLambdaException
Lambda.SdkClientException

- History of each run


- Visual Monitoring


- High volume orchestration


#### Standard and Express Workflow

Standard Workflow are ideal for long-running,m durable and auditable workflows

Express workflow are ideal for high-volume, event procesing workloads such as IoT data ingestion,
streaming data processing and transformation

- There are 2 types of express workflow-> async and sync.

| | Standard Workflow | Express workflow|
|-| ----------------- | --------------- |
|Maximum duration | 1 year | 5 minutes |
| Workflow run start rate | over 2000 per seconds | over 100000 per second|
| Start transition rate | Over 4000 per seconds per account | Nearly unlimited|
| Workflow run semantics | Exactly one workflow run | Sync: at-most-once workflow run, asyn: at least one workflow run|
| Service integrations | Supports all service integrations and patterns | Id does not support job-run(.sync) or Callback(waitForTaskToken)


