Install Tools

# Update homebrew
brew update

# Docker
# https://www.docker.com/community-edition
brew cask install docker

# jq
# https://stedolan.github.io/jq/
brew install jq

# yq
# https://yq.readthedocs.io/en/latest/
pip3 install --upgrade yq

# uuid
# https://github.com/kelektiv/node-uuid
npm install -g uuid

# awscli
# http://docs.aws.amazon.com/cli/latest/reference/
pip3 install --upgrade awscli

# awslogs
# https://github.com/jorgebastida/awslogs
pip3 install --upgrade awslogs

# aws-rotate-key
# https://github.com/Fullscreen/aws-rotate-key
brew tap fullscreen/tap
brew install aws-rotate-key

# envsubst
brew install gettext
brew link --force gettext 


# dos2unix
brew install dos2unix

# virtualenv
# https://virtualenv.pypa.io/en/stable/
pip3 install --upgrade virtualenv

# nvm
# https://github.com/creationix/nvm
curl -kLs -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh \
| PROFILE="${HOME}/.bashrc" bash
Configure AWS CLI
CLI Reference: https://docs.aws.amazon.com/cli/latest/reference/index.html
Configuration Reference: https://docs.aws.amazon.com/cli/latest/reference/configure/index.html
Configuration Guide: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html
Configuration Variables: https://docs.aws.amazon.com/cli/latest/topic/config-vars.html
Configure Access, Secret and Profiles
# Create ~/.aws
mkdir -p ~/.aws && chmod 0755 ~/.aws
touch ~/.aws/config && chmod 0644 ~/.aws/config
touch ~/.aws/credentials && chmod 0600 ~/.aws/credentials

# Enable CloudFront Preview
aws configure set preview.cloudfront true

#
# Set profile name
#   - If you access multiple account, repeat this step and the configuration
#     section below
_aws_profile=xxxxx

# Set configurations
aws configure set region us-east-1 --profile ${_aws_profile}
aws configure set output json --profile ${_aws_profile}
aws configure set ca_bundle ${HOME}/xxxxx/ca-bundle.pem --profile ${_aws_profile}

# Set Access/Secret keys
#   If you do not know how to obtain the access and secret, please review
#   the "To get your access key ID and secret access key" section here:
#   https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-quick-configuration
aws configure set aws_access_key_id XXXXXXXXXXXXXXXXXX --profile ${_aws_profile}
aws configure set aws_secret_access_key XXXXXXXXXXXXXXXXXX --profile ${_aws_profile}

# Add the following environment variable to ~/.bashrc
#   - Set this to your most frequently used profile
#   - If you have only one, set it to that
echo 'export AWS_DEFAULT_PROFILE=xxxxx' >> ~/.bashrc

# Source ~/.bashrc to load the environment variable from above
source ~/.bashrc

# Verify Configurations and Access
aws iam get-user
Rotating Access Keys
It is recommended to do this every 30 days
General overview of the process is detailed here: https://aws.amazon.com/blogs/security/how-to-rotate-access-keys-for-iam-users/
# Rotate keys for a specific profile
aws-rotate-key -profile xxxxx -y


MFA Login
Typically, most non-trivial operations will require you to have authenticated using an MFA Token.

# Get a new session token with MFA
#   - This will typically be valid for 12 hours
eval $(aws-mfa-login -p xxxxx-t XXXXXX)
The following process will allow you to use MFA against multiple accounts:


# Add a utility function to ~/.bashrc
echo 'function aws-use-profile { local profile=$1;local sessions_dir="${HOME}/.aws/sessions";[[ -n "${AWS_SESSIONS_DIR}" ]]&&sessions_dir="${AWS_SESSIONS_DIR}";local sessions_env="${sessions_dir}/${profile}.env";[[ -f "${sessions_env}" ]]&&source "${sessions_env}"&&return 0;export AWS_DEFAULT_PROFILE="${profile}";return 0;}' >> ~/.bashrc
x
Configure Aliases
The AWS CLI allows you to configure various command aliases. There is hardly any documentation on this useful feature. There are some examples available in the awslabs repo.


# Create a file to hold aliases
mkdir -p ~/.aws/cli
touch ~/.aws/cli/alias

# Create some sample aliases
cat >~/.aws/cli/alias <<_EOL
# AWS CLI Aliases
# See: https://github.com/awslabs/awscli-aliases/blob/master/alias

[toplevel]

whoami = sts get-caller-identity
whereami = iam list-account-aliases --query AccountAliases[0] --output text
_EOL

# Try using the aliases ...

# This should print who you can currently logged in as. Useful if you have assumed a role
aws whoami

# This should print the account you are currently logged in to
aws whereami
