#### Integratin EventBridge with other services

There are 3 sources events for EventBridge

- AWS Services
- SaaS Partners
- Custom applications


| Event Source | Event Bus | Uses |
| ------------ | --------- | ---- |
| AWS Services | Default   | AWS services in the same account and Region all send events to the default event bus | 
| SaaS Partners | Partner  | Each SaaS partner has a partner event bus to receive events|
| Custom applications | Custom | Custom applications you build can send and receive events using custom event bus.|

For a custom event,you are required to contain the following fields: "source", "detail", "detail-type"

### Benefits of a single target for each rule
- Reduce complexity
- Easier troubleshooting
- Each event bust can have up to 300 rules as the default limit.

### Security reliability

- IAM for eventbus
- Retry policy - {Deadletter queue}

Replay could be used to store and test scenarios 
