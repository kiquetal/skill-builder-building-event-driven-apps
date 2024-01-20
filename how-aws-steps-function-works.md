### How AWS Step Functions work

| Standard | Express|
| -------- | ------ |
| Long-running with access to visualization and full history in the console| Short-running with access to results in Amazon Cloudwatch Logs|
| Exactly-once execution model | Asynchronus(at least one execution model) Synchronous(at most once execution model)|
| Execution state internally persisted on every state transition | No internally persisted state for asynchronus exectuonsState machine logic must be idempotent | 
| Ideal for long-running, durable and auditable workflows such as starting an EMR cluster or procesing payments | Ideal for high-volume event-processing workloas such as IoT data ingestion, streaming data processing and transformation, and mobile application backends|


