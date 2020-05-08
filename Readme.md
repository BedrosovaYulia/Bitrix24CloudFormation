1) To create your EC2 instance for Bitrix24 using CloudFormation, first 
change Private IP on yours, next save CF_Template.yml to your own S3 bucket, 
then update the command below to reference your bucket as well as the name of a Key pair that you own in the 
region that you are working in. 

aws cloudformation create-stack --stack-name CodeDeployB24Stack \
--template-url http://s3-region.amazonaws.com/bucket-name/CF_Template.yml \
--parameters ParameterKey=KeyName,ParameterValue=key_name \
--capabilities CAPABILITY_IAM

2) Verify that the Cloud Formation stack has completed using: 
aws cloudformation describe-stacks --stack-name CodeDeployB24Stack --query "Stacks[0].StackStatus" --output text

3) After installation password for root and bitrix will be: bx24thebest
