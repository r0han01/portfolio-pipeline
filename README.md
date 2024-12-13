# Web App Portfolio - AWS CodePipeline

This repository demonstrates a simple web application deployment using AWS CodePipeline. The pipeline automates the process of pulling code from GitHub, building the project with AWS CodeBuild, and deploying the build to an Amazon S3 bucket.

## Overview

The pipeline consists of three main stages:

1. **Source**: Retrieves the latest code changes from the GitHub repository.
2. **Build**: Uses AWS CodeBuild to build the application (for now, simply processes the `index.html` file).
3. **Deploy**: Deploys the built application to an Amazon S3 bucket.

### Repository Structure

The repository contains the following files:

- **index.html**: The HTML file for the web application (most recently updated).
- **buildspec.yml**: A build specification file used by AWS CodeBuild to define the build process.

### Setup Instructions

To replicate this pipeline in your own AWS environment:

1. **Create the GitHub repository**: Ensure that your project repository is linked with GitHub.
   
2. **Create an S3 Bucket**: The application will be deployed to an S3 bucket. If you haven't created one, go to the S3 console in AWS and create a new bucket.

3. **Create a CodePipeline**: Set up AWS CodePipeline to automate the workflow. This pipeline will have three stages:
   - **Source Stage**: Connect the GitHub repository as the source.
   - **Build Stage**: Use AWS CodeBuild with the `buildspec.yml` file to define how the application is built.
   - **Deploy Stage**: Use Amazon S3 as the deployment target.

### Buildspec.yml Explanation

The `buildspec.yml` file defines the commands used by CodeBuild to build the application. Below is an example of what it might look like:

```yaml
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: 14
  build:
    commands:
      - echo Building the project...
      - # Add any build steps required (e.g., compiling, testing)
artifacts:
  files:
    - index.html
