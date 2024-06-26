# AWS CodeDeploy Documentation

## Overview

This repository contains a guide for deploying a web application using AWS CodeDeploy. It includes detailed steps for setting up EC2 instances, configuring VPC, writing deployment scripts, creating a CodeDeploy application, and managing deployment groups. 

## Introduction

AWS CodeDeploy is a service that automates code deployments to any instance, including Amazon EC2 and on-premises servers. Developers and teams use AWS CodeDeploy because it simplifies deployment, reduces downtime, and integrates easily with existing CI/CD tools, ensuring faster and more reliable releases.

## Setup Guide

### Set up EC2 Instance and VPC

To set up an EC2 instance and VPC, use AWS CloudFormation to create the required resources. This setup creates a separate environment for your production deployment.

### Write Bash Scripts

Create the following Bash scripts for the deployment process:

1. `install_dependencies.sh`: Installs Tomcat and HTTPD (web servers)
2. `start_server.sh`: Starts the web servers
3. `stop_server.sh`: Stops the web servers

### Create CodeDeploy IAM Role

Create an IAM service role for CodeDeploy using an AWS Managed Policy called `AWSCodeDeployRole`, which adds the necessary permissions for CodeDeploy to access other AWS services.

### Create CodeDeploy Application

Create a CodeDeploy application and select the compute platform, such as EC2, to host your web application. This setup allows you to configure how your application will be deployed.

### Set up Deployment Group

Configure your deployment group with the following settings:

- **Service Role**: IAM role for the deployment group to give CodeDeploy access to your EC2 instance.
- **Deployment Type**: Choose 'In place' to deploy the latest web app directly to the existing environment.
- **Environment Configuration**: Use Amazon EC2 instances.
- **CodeDeploy Agent**: Ensure it communicates with your EC2 Web Server for deployment instructions.
- **Deployment Settings**: Configure whether deployment will be staggered or done all at once.
- **Load Balancer Setting**: Disable if using a single web server.

### Kick off Deployment

Set up a revision location for your web app's build artifacts, such as a Java WAR file in an S3 bucket. Deploy the application by visiting your EC2 instance’s IPv4 address to see the web app in action.

## Key Learnings

1. **Automating Deployments**: Ensures new code changes are reliably and consistently delivered with minimal downtime.
2. **Environment Separation**: Allows for thorough testing and validation of changes in a controlled setting before going live.
3. **AWS Resource Setup**: Involves creating an EC2 instance, writing scripts, configuring IAM roles, and setting up CodeDeploy applications and deployment groups.
4. **Smooth Deployment Process**: Setting up the deployment pipeline correctly ensures a seamless and automated deployment process.

## Contact

Feel free to reach out:

- GitHub: [KanikaGenesis](https://github.com/KanikaGenesis)
- LinkedIn: [Kanika Mathur](https://www.linkedin.com/in/kanika-mathur-083080121)

