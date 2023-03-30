# Initial playing around with localstack and terraform

cd terraform 
tflocal init
tflocal apply

Remember to reference the terraform.tfstate and also https://app.localstack.cloud/
Remember with localstack that you'll be accessing the resources on port 4566

Website is http://<s3name>.s3-website.localhost.localstack.cloud:4566/

NOTES:
The outputs.tf file should be mandatory given it provides clear ways of seeing localstack resources
