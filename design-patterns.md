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
