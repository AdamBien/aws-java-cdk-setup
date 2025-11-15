# CDKv2 for Java Setup

Step-by-step configuration for AWS CDK with Java.

## Prerequisites

Before starting, ensure you have the following installed:

- **Java 25** - [Download Java](https://www.oracle.com/java/technologies/downloads/)
- **Maven** - [Maven Installation Guide](https://maven.apache.org/install.html)
- **Node.js** (v18 or later) - Required for CDK CLI - [Node.js Downloads](https://nodejs.org/)

📚 **Documentation**: [AWS CDK Prerequisites](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_prerequisites)

## AWS Credentials Setup

### Obtain Credentials from AWS Access Portal

If your organization uses AWS IAM Identity Center (formerly AWS SSO):

1. Navigate to your AWS Access Portal URL (provided by your administrator)
2. Sign in with your credentials
3. Select the AWS account you want to access
4. Click on "Access Keys"
5. Copy the credentials from: "Option 1: Set AWS environment variables" and pastem them to the terminal

📚 **Documentation**: [AWS IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)

### Configure AWS CLI Credentials

## Tool Installation

### Install AWS CLI

On macOS using Homebrew:

```bash
brew install awscli
```

Verify installation:

```bash
aws --version
```

Expected output: `aws-cli/2.x.x ...`

📚 **Documentation**: [Installing AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

### Install AWS CDK CLI

Install CDK CLI globally using npm:

```bash
npm install -g aws-cdk
```

Verify installation:

```bash
cdk --version
```

Expected output: `2.x.x (build ...)`

📚 **Documentation**: [Installing AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_install)

## Environment Bootstrap

Paste the credentials into the terminal before running the commands below.

Bootstrap your AWS environment for CDK deployments. This creates necessary resources (S3 bucket, IAM roles) in your AWS account:

```bash
cdk bootstrap aws://ACCOUNT-NUMBER/REGION
```

Example:

```bash
cdk bootstrap aws://123456789012/us-east-1
```

Or let CDK determine your account and region automatically:

```bash
cdk bootstrap
```

Expected output:
```
 ⏳  Bootstrapping environment aws://123456789012/us-east-1...
 ✅  Environment aws://123456789012/us-east-1 bootstrapped.
```

**What does bootstrap create?**
- S3 bucket for storing CDK assets (Lambda code, Docker images)
- IAM roles for CloudFormation deployments
- ECR repository for container images (if needed)

📚 **Documentation**: [Bootstrapping CDK](https://docs.aws.amazon.com/cdk/v2/guide/bootstrapping.html)

## Verification

Verify your setup by deploying a working example project:

```bash
git clone https://github.com/AdamBien/aws-quarkus-lambda-function-url-cdk-plain.git
cd aws-quarkus-lambda-function-url-cdk-plain
```

Follow the deployment instructions in that repository to confirm your environment is properly configured.

📚 **Documentation**: [Deploying CDK Applications](https://docs.aws.amazon.com/cdk/v2/guide/deploy.html)

📚 **Documentation**: [AWS CLI Configuration Troubleshooting](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-troubleshooting.html)

