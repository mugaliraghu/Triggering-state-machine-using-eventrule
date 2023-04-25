## Object
This is a CloudFormation template written in YAML format. It creates a serverless application pattern that uses AWS EventBridge and AWS Step Functions to monitor and respond to changes in the state of an Amazon instance.The template defines a single resource, a Serverless State Machine called "EC2StateWatcher". The State Machine has a set of States that are defined using AWS Step Functions' JSON-based state language. The States include a Choice state, "What Happened?", that is used to determine the next state to transition to based on the state of the EC2 instance. The States also include three Pass states, "It's Running", "It's Stopped", and "It's Gone", that are used to represent the end states of the State Machine.
The State Machine is triggered by an AWS EventBridge rule called "StateChange". The rule is configured to listen for events on the default event bus for EC2 instances that have changed state to "running", "stopped", or "terminated". The input to the State Machine is set using the "InputPath" property of the EventBridge rule, which selects the "detail" field of the event object.

## Steps
Go where the template.yaml file is present and perform the command, it will validate SAM template and build.

```t
sam build
```
after use the command, it will creates the resources that we given in template file.

```t
sam deploy --guided
```

check the cloudformation stack with the stack name that you given while deploying the application.
![Screenshot (50)](https://user-images.githubusercontent.com/120295902/234185277-224f1249-6bf0-4c5f-a070-0230fa686d19.png)

## Validation steps
The instance which is showing here in a stopped state.
<img width="842" alt="instance_stopped state" src="https://user-images.githubusercontent.com/120295902/234184046-3fa98c3e-3336-4bf1-ab28-d1139b1ff95c.png">

After starting instance go to state machine console logs, check the status, it has to running status.
![Screenshot (48)](https://user-images.githubusercontent.com/120295902/234185255-eae6f782-1337-40ec-b881-424b8530e257.png)

and again i stopped the instance, and the status is as shown in below image.
![Screenshot (50)](https://user-images.githubusercontent.com/120295902/234185644-b7d9a207-623c-4e3b-8eb3-07838bd24f62.png)

