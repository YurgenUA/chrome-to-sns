# Chrome to SNS

This repository (will eventually) contains the source code for a Chrome Plugin which is capable of capturing metadata about the current Chrome Tab, and transmit messages to a lightweigtht API which places the message on an SNS topic.

Solution can be deployed with Terraform command:
terraform apply -auto-approve -var-file="setup.tfvars"

#### Please amend variables in file "setup.tfvars" before deploying
```
REGION = "eu-north-1"
STAGE = "dev" // <- idea for this var is to distinguish deploymends on dev/stg/prod
TOPIC_NAME = "chrome-activity" // <- AWS SNS topic name to create
```

## Testing

1. sns.test.py is integration test which creates SQS queue, subscribes it to SNS topic, posts message to SNS and reads it from SQS. All created resources are cleared at the end.
2. curl-manual-test.txt is API Gateway deployment test doing ok/failed requests. URL should be amended to pint to your deployment before run.