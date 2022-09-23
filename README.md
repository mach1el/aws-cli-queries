# AWS cli queries
This is note for aws-cli commands 

## EC2

* Get instance id,name
```
aws ec2 describe-instances --query 'Reservations[].Instances[].{source_id:InstanceId,name:Tags[?Key==`Name`]|[0].Value}' --output json
```
*Filter example*: `--filters 'Name=tag-value,Values=your_value' 'Name=instance-state-name,Values=running'`
