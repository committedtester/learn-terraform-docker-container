# Quick Version

For the full setup please

cd terraform
tflocal init
tflocal apply

Remember to reference the terraform.tfstate and also https://app.localstack.cloud/
Remember with localstack that you'll be accessing the resources on port 4566

The repository also contains a pre-commit hook
    pip install pre-commit
    pre-commit install
