#### Introduction to AWS Step Functions

- AWS Step Functions provides serverless orchestration for modern applications. Orchestration centrally
manages a workflow by breaking it into multiple stepds, adding flow logic, and tracking the inputs
and output between the steps. As your application runs, Step Functions maintains the application state,
tracking exactly which workflow step your application is in, and stores an event log of data that is passed
between application components. 

- State: A state machine is a workflow. A task is a state in a workflow that represents a single unit of work that
another AWS service perfoms. Each step in a workflow is a state.
Individual states can make decisions based on their input, perfom actions, and pass output to other states.

States can provide a variety of functions in your state machine:
- Perfom some work in your state machine
- Make a choice between branches of activity
- Stop an activity with a failure or sucess.
- Simply pass its input to its output or inject some fixed data.
- Provide a delay for a certain amount of time or until a specified time or date.
- Begin parallel branches of activity.
- Dynamically iterate steps.

#### Types of states

- Pass State: passes its input to its output, without performing work. Pass states are useful when constructing and debugging
state machines.

- Task State: represent a single unit of work performed by a state machine. Tasks perform all work in your state machine. A task
perfoms work by using an activity or an AWS Lambda function, or by passing parameters to the API actions of other services.

- Choice State : add branching logic to a state machine

- Wait State: Delay the state machine from continuing for a specified time. You can choose either a relative time, specified in seconds
from when the state begins, or an absolute end timime, specified as timestamp

- Succeed state: Stop an activity successfully. The Succeed state is a useful target for Choice state branches that don't do anything
except stop the activity. Because Succeed states are terminal states, they have no Next field, and don't need an End field.

- Fail State: Stops the activity of the state machine and marks it as failure, unless it is caught by a Catch block.

- The parallel state: Can be used to create parallel branches of activity in your state machine.

- Map State: can be used to run a set of steps for each element of an input array. While the Parallel state invokes multiple branches
of steps using the same input, a Map State will invoke the same steps for multiple entries of an array in the state input.



- 
