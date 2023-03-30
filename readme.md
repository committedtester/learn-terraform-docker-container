# Quick Version

For the full setup please refer to readme_wsl2.md

* cd terraform
* tflocal init
* tflocal apply

Remember to reference the terraform.tfstate and also https://app.localstack.cloud/ for deployment information.

Remember with localstack that you'll be accessing the resources on port 4566

# Pre-commit hook
The pre-commit hook that formats and generates terraform documentation requires
* pip install pre-commit
* pre-commit install
* git add .pre-commit-config.yaml

## Or to execute pre git commit
* pre-commit run -a