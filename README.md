# AWS cli queries
This is note for aws-cli commands 

## EC2

* Get instance id,name
```
aws ec2 describe-instances \
  --query 'Reservations[].Instances[].{source_id:InstanceId,name:Tags[?Key==`Name`]|[0].Value}' \
  --output json
```
**Filter example**: `--filters 'Name=tag-value,Values=your_value' 'Name=instance-state-name,Values=running'`

* Get amis
```
aws ec2 describe-images --query 'Images[].ImageId'
```
**Filter example**: `--filter Name=owner-id,Values=123456789`

* Get IP
```
aws ec2 describe-network-interfaces --query 'NetworkInterfaces[*].PrivateIpAddress'
```
**Filter example**: `--filters "Name=subnet-id,Values=subnet-123456"`

* Get Security Groups IDs
```
aws ec2 --profile jayesongroup describe-security-groups --query "SecurityGroups[*].GroupId" 
```
