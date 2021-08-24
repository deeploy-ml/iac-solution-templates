# Create Deeploy Stack from AWS CloudFormation Template
> This repostory currently is able to create the Deeploy stack except the EKS cluster

This CloudFormation template allows you to deploy the Deeploy Stack on Azure. It creates 2 resource groups:
* [IAM user with rights to access the created KMS key and S3 Bucket](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html#intro-identity-users)
* [PostgreSQL RDS managed Database](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
* [S3 Bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
* [KMS Key with Alias](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)

Run (parameter values are defaults):

```
aws cloudformation create-stack \
--stack-name deeployio \
--template-body file://aws.template \
--parameters \
ParameterKey=name,ParameterValue=deeploy \
ParameterKey=callingUserArn,ParameterValue="$(aws sts get-caller-identity --query Arn --output text)" \
ParameterKey=deeployUser,ParameterValue=deeploy \
ParameterKey=DBName,ParameterValue=deeploy \
ParameterKey=DBUser,ParameterValue=deeploy \
ParameterKey=DBPassword,ParameterValue=<your-password> \
ParameterKey=DBAllocatedStorage,ParameterValue=5 \
ParameterKey=DBInstanceClass,ParameterValue=db.t2.small \
ParameterKey=S3BucketName,ParameterValue=deeployio \
--capabilities CAPABILITY_NAMED_IAM
```

After the creating the cloudformation template the IAM keys are available as output (and can be used in the Deeploy Helm chart)