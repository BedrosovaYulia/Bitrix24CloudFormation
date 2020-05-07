1) To create your EC2 instance for Bitrix24 using CloudFormation, first save CF_Template.yml to your own S3 bucket, 
then update the command below to reference your bucket as well as the name of a Key pair that you own in the 
region that you are working in. 

WINDOWS users will need to use ^ (Shift + 6) instead of \ for line continuation.

aws cloudformation create-stack --stack-name CodeDeployDemoStack \
--template-url http://s3-region.amazonaws.com/bucket-name/CF_Template.yml \
--parameters ParameterKey=KeyName,ParameterValue=key_name \
--capabilities CAPABILITY_IAM

2) Verify that the Cloud Formation stack has completed using: 
aws cloudformation describe-stacks --stack-name CodeDeployDemoStack --query "Stacks[0].StackStatus" --output text

3) Log in to your instance and check that the CodeDeploy agent has correctly installed:  
sudo service codedeploy-agent status
