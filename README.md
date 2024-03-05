# Deployment of Static Website to AWS S3 Bucket using GitHub Workflows

This project demonstrates how to automate the deployment of a static website built with CSS, HTML, and JavaScript to an AWS S3 Bucket using GitHub Workflows.

## Overview

Static websites, which consist of HTML, CSS, and JavaScript files, can be hosted on AWS S3 Buckets. This deployment process is made simple and automated using GitHub Workflows. With GitHub Workflows, you can trigger actions such as building, testing, and deploying your code whenever changes are pushed to your GitHub repository.

## Prerequisites

Before getting started, make sure you have the following:

- A GitHub account
- An AWS account
- Static website files (HTML, CSS, JavaScript, etc.) stored in your GitHub repository

## Deployment Steps

1. **Prepare your Static Website**: Ensure that your static website files, including HTML, CSS, JavaScript, and any other assets, are ready for deployment. These files should be stored in your GitHub repository.

2. **Configure AWS Credentials**: Set up AWS credentials in your GitHub repository secrets to allow GitHub Actions to access your AWS account. This step is necessary for deploying your static website to an S3 Bucket.

3. **Create GitHub Workflow**: Create a GitHub Workflow file (e.g., `deploy.yml`) in the `.github/workflows` directory of your repository. This workflow file defines the steps to be executed by GitHub Actions when triggered. It includes steps to checkout code, configure AWS credentials, and deploy static files to the S3 Bucket.

4. **Test Workflow**: Test your GitHub Workflow to ensure that it runs successfully and deploys your static website to the AWS S3 Bucket as expected. You can do this by pushing changes to your repository and monitoring the workflow execution in the Actions tab of your GitHub repository.

## Example Workflow File

Here's an example of a GitHub Workflow file (`deploy.yml`) that deploys static files to an S3 Bucket:

```yaml
name: Deployment

on:
  push:
    branches:
    - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v1

    - name: Configure AWS Credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: <your-aws-region>

    - name: Deploy static site to S3 bucket
      run: aws s3 sync . s3://<your-bucket-name>
```

## Workflow Steps:


![Screenshot (187)](https://github.com/safuvanh/Github-Workflow-AWS-S3/assets/156053146/c6c43e9b-ff51-4fb8-8530-85702055aa4a)

## Deployment:

![Screenshot (183)](https://github.com/safuvanh/Github-Workflow-AWS-S3/assets/156053146/8a7a7aaa-5cee-444e-a86c-515e5cd66580)

## Output

- Make public the all Objects stored in S3 Bucket using ACL
- Copy Index.html object Url and Browse

  ![Screenshot (185)](https://github.com/safuvanh/Github-Workflow-AWS-S3/assets/156053146/c28568bb-cb6d-4b9f-83b6-aeb0bd6cedeb)
  ![Screenshot (186)](https://github.com/safuvanh/Github-Workflow-AWS-S3/assets/156053146/67adfe7c-2589-41ac-806f-8569a95a7ef2)


  




