# Dynamo PITR Experiment

Can you add PITR to an existing DB without breaking it?
Yes? I think so?

## Steps

### Provision the DB (No PITR yet, it's commented out)

```shell
aws cloudformation create-stack \
--stack-name $(whoami)-pitr-experiment \
--region us-east-2 \
--template-body file://dynamo-template.yaml
```

### Add Records to the Database

Via the AWS web console.

### Uncomment The Following

```yaml
PointInTimeRecoverySpecification:
   PointInTimeRecoveryEnabled: true
```

### Update the Cloudformation Stack

```shell
aws cloudformation update-stack \
--stack-name $(whoami)-pitr-experiment \
--region us-east-2 \
--template-body file://dynamo-template.yaml
```

### Use AWS Web Console To Validate Records Exist
