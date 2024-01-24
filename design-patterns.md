### Design Pattern Event Bridge

#### Parallel state field options

- Branches is required field that contains an array of objects that your state machine should execute in parallel. Each of these state machine must hava fields
names States and StartAt

- ResultPath is an optional field that you can use to control which combinaqtion of both input and the results are passed to the state output. By using
ResultPath with the Parallel state, you can control what information passes to the output.

- ResultSelector is an optional field you can use to manipulate results before you apply the ResultPath.If ResultSelector is used, this will replace
the state's result and only the data selected will be passed to ResultPath.

- Catch is an optional field that you can use to define a fallback state to be rn if the state encounters a defined error.

- Retry is an optional field you can use after an error in your state machine is caught to implement a retry. This can limit the amount of human
intervention needed to resolve errors in your application.

```json

{
  "Comment": "Parallel Example.",
  "StartAt": "LookupCustomerInfo",
  "States": {
    "LookupCustomerInfo": {
      "Type": "Parallel",
      "End": true,
      "Branches": [
        {
         "StartAt": "LookupAddress",
         "States": {
           "LookupAddress": {
             "Type": "Task",
             "Resource":
               "arn:aws:lambda:us-east-1:123456789012:function:AddressFinder",
             "End": true
           }
         }
       },
       {
         "StartAt": "LookupPhone",
         "States": {
           "LookupPhone": {
             "Type": "Task",
             "Resource":
               "arn:aws:lambda:us-east-1:123456789012:function:PhoneFinder",
             "End": true
           }
         }
       }
      ]
    }
  }
}
``` 
#### Dynamic parallelism


Map state field options

- An iterator
- ItemsPath: The JSONPath that identifies the array to iterate over
- MaxConcurrency: The maximum number of iterations that can run in parallel
- ResultPath: is an optional field that you can use to control which combination of both
the input and the results are passed to the state output. By using ResultPath with the Map
state, you can control what information passes to the output.
- ResultSelector: is an optional field you can use to manipulate results before you apply
the ResultPath. If ResultSelector is used, this will replace the state's result and only the
data selected will be passed to ResultPath.
- Catch: is an optional field that you can use to define a fallback state to be run if the state
encounters a defined error.
- Retry: is an optional field you can use after an error in your state machine is caught to
implement a retry. This can limit the amount of human intervention needed to resolve errors
in your application.


#### Nested design pattern for Step Functions

- Separate higher-level workflows from lower level, task-specific workflows
- Avoid repetitive elements by calling a separate state machine multiple times.
- Create a library of modular, reusable workflows for faster development
- Reduce workflow complexity and make it easier to edit and troubleshoot state machines
- Reduce the costs of workflow executions by using Standard and Express workflows

#### Orchestrastion and choreography

Dividing the application into different business domains, each with its own bounded context,
simplifies management of large, complex applications. You can also use these separate business
domains to invoke different workflows depending on the type of order that must be fulfilled.


| Orchestration | Choreography |
| ------------- | ------------ |
| Steps functions workflows are composed of taks tat represent a single unit of work that another AWS service performs.With Step functions the state of each step in your workflow is invoked 
to make sure that your application runs in order and as expected| When the orchestrarot publishes an event from the results of a workflow, you will need a way to act on these results
Each orchestrator only knows what is happening within its own workflow and knows nothing about the previous of future steps in the application.The choreography component coordintes
these transitions and lets you move through other subdomains using events |

The Wait-for-callback is only supported by Standard Workflows


#### Saga design patterns

The SAGA design pattern is a failure management pattern that helps establish consistency in distributed applications and coordinates transactions
between multiple microservices to maintain data consistency. When you use the saga pattern, every service that perfoms a transaction
publishes an event that inovkes subsequent services to perfom the next transcation in the chain.

Uses cases of SAGA design pattern

- The application needs to maintain data consistency across multiple microservices without tight coupling
- There are long-lived transactions and you don´t want other microservices to be blocked if one microservices runs for a long time.
- You need to be able to roll back a transaction if one of the microservices fails.



