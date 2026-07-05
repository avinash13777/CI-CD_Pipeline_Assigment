**********Assignment 1 – Jenkins CI/CD Pipeline for Flask Application******************
Objective

Implement a CI/CD pipeline using Jenkins to automate the build, test, and deployment of a Flask application.

**Process & Actions**
1. Repository Setup
Forked the provided Flask application repository into GitHub.
Cloned the forked repository to the local machine.
Verified the repository structure.

2. Environment Preparation
Installed Python 3.
Created a Python virtual environment.
Activated the virtual environment.
Installed all project dependencies using:
requirements.txt

3. Configure Flask Application
Added MongoDB Atlas connection.
Created a .env file containing:
MONGO_URI
SECRET_KEY
Used python-dotenv to load environment variables.
Configured Flask to read the MongoDB URI from the environment.

4. Configure Application Startup
Created the start_flask.sh script.
Script performs:
Creates virtual environment (if not available)
Activates virtual environment
Installs Python packages
Starts the Flask application
Runs the application in the background

5. Create Jenkins Pipeline

Created a Jenkinsfile with three stages:

Build Stage
Create virtual environment
Upgrade pip
Install dependencies
Test Stage
Execute unit tests using:
pytest
Deploy Stage
Execute:
start_flask.sh
Deploy the Flask application
Post Actions
Display success message when pipeline completes successfully.
Display failure message if any stage fails.

6. Configure Jenkins
Created a new Pipeline project.
Connected Jenkins with the GitHub repository.
Configured:
Git Repository URL
Branch
Jenkinsfile location
Saved the project.

7. Execute Pipeline
Triggered the Jenkins build.
Pipeline executed in the following order:
Build
Test
Deploy
Verified successful pipeline execution.



*****************************Assignment 2 – GitHub Actions CI/CD Pipeline for Flask Application***************************
Objective

Implement an automated CI/CD workflow using GitHub Actions for a Flask application.

Process & Actions
1. Repository Preparation
Used the existing GitHub repository.
Verified the repository contains:
main branch
staging branch
2. Create GitHub Actions Workflow

Created the directory:

.github/workflows/

Added the workflow file:

python-ci-cd.yml
3. Configure Workflow Triggers

Configured the workflow to execute on:

Push to main
Push to staging
Release publication
4. Build & Test Job

Configured the workflow to:

Checkout repository
Setup Python
Create virtual environment
Upgrade pip
Install dependencies
Run syntax validation
Build the application
5. Configure Environment Variables

Used GitHub Secrets for secure credentials.

Created Repository Secrets:

MONGO_URI
SECRET_KEY

Loaded them inside the workflow using:

env:
  MONGO_URI: ${{ secrets.MONGO_URI }}
  SECRET_KEY: ${{ secrets.SECRET_KEY }}
6. Configure Staging Deployment

Created the deploy-staging job.

Execution condition:

Trigger only when code is pushed to the staging branch.

Deployment action:

Display staging deployment message.
Simulate deployment completion.
7. Configure Production Deployment

Created the deploy-production job.

Execution condition:

Trigger only when a Release is published.

Deployment action:

Display production deployment message.
Simulate deployment completion.
8. Push Workflow to GitHub
Added workflow YAML file.
Committed the workflow.
Pushed changes to GitHub.
9. Verify GitHub Actions

Verified workflow execution on:

Push to main
Push to staging
Release event

Confirmed successful completion of:

Build
Staging Deployment (for staging)
Production Deployment (for Release)
10. Create GitHub Release

Created a Release using:

Existing Git Tag
Release Title
Release Notes

Published the Release.

11. Verify Production Deployment

Confirmed that the Release automatically triggered:

Build Job
Production Deployment Job

Verified successful execution in the GitHub Actions tab.
8. Version Control
Committed all project changes.
Pushed updated code to GitHub.
