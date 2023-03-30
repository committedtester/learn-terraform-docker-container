Install locally

https://chocolatey.org/install#individual
Or to upgrade
```none
choco upgrade chocolatey
```

Install
```none
choco install wsl2
wsl --install -d ubuntu
```

for pyenv in wsl2
(from https://www.techtronic.us/install-python-pyenv-on-wsl-ubuntu/ and https://medium.com/geekculture/how-to-install-and-manage-multiple-python-versions-in-wsl2-6d6ce1b6f55b)
```none
sudo apt-get update --yes
sudo apt-get install --yes git

sudo apt-get install git gcc make openssl libssl-dev libbz2-dev libreadline-dev libsqlite3-dev zlib1g-dev libncursesw5-dev libgdbm-dev libc6-dev zlib1g-dev libsqlite3-dev tk-dev libssl-dev openssl libffi-dev

curl https://pyenv.run | bash
```

We now need to update the .profile and .bashrc to have this available for all terminals as per the installation information
```
# Load pyenv automatically by appending
# the following to
~/.bash_profile if it exists, otherwise ~/.profile (for login shells)
and ~/.bashrc (for interactive shells) :

export PYENV_ROOT="$HOME/.pyenv"
command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# Restart your shell for the changes to take effect.

# Load pyenv-virtualenv automatically by adding
# the following to ~/.bashrc:

eval "$(pyenv virtualenv-init -)"
```

Install latest python

```
# to avoid the ModuleNotFoundError: No module named '_lzma' error
sudo apt-get install liblzma-dev

pyenv install 3.11
pyenv global 3.11
```

Install pip
```
sudo apt update
sudo apt upgrade
sudo apt install python3-pip
pip install --upgrade pip
pip3 --version
```

Install localstack
```
pip install localstack
```

Run localstack
```
localstack start -d
```

If you hit errors in relation to "We recommend to activate the WSL integration in Docker Desktop settings. For details about using Docker Desktop with WSL 2, visit: https://docs.docker.com/go/wsl2"
```
## Within powershell set the default distro to ubuntu
wsl.exe -l -v
wsl --set-default ubuntu
wsl.exe -l -v
```

Next update Vs Code to work with WSL
Install the Remote Development Extension and then restart the application

**Install Terraform**
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

Create directory in the aaronmckay home directory and follow the quick start tutorial

Install AWS CLI as per
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
```
sudo apt install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

Run aws configure with test for the access and secret keys

Using a terraform file of
```
resource "aws_s3_bucket" "test-bucket" {
  bucket = "my-bucket"
}
```

Run
```
terraform init
terraform plan
terraform apply
```

Also confirm the tflocal wrapper which will convert terraform to localstack
```
pip install terraform-local
tflocal init
tflocal apply
```

Then to view the bucket afterwards
```
aws --endpoint-url=http://localhost:4566 s3 ls
```

Or to simplify this down
```
pip install awscli-local
awslocal s3 ls
```

For the pre-commit
```
pip install pre-commit
pre-commit install
```

Create a .pre-commit-config.yaml file with
```
repos:

-   repo: https://github.com/pre-commit/pre-commit-hooks

    rev: v2.3.0

    hooks:

    -   id: check-yaml

    -   id: end-of-file-fixer

    -   id: trailing-whitespace

-   repo: https://github.com/psf/black

    rev: 22.10.0

    hooks:

    -   id: black
```

Then run
```
pre-commit run --all-files
```

To avoid this error in bash output in git "bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)"
```
sudo apt install locales locales-all
```
