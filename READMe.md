# Change to trigger web-hook
# Made changes in dev branch again
# Another change

# Building a Continuous Integration and Continuous Delivery/Deployment (CICD) Pipeline

![](img/jenkins_diagram.png)

![](img/CICD_diagram.png)

![](img/cicd_jenkins_diagram.png)

For deployment job in Jenkins
In the execute shell of CD job
- we need to by pass the key asking stage with below command:
ssh -A -o "StrictHostKeyChecking=no" ubuntu@ec2-ip << EOF	

- create an env to connect to db
- navigate to app folder
- kill any existing pm2 process just in case
- launch the app

## Setting up an SSH Key between GitHub and Jenkins
### Step 1: Create a new key
- Go into .ssh directory
`cd ssh`
- 

## Create a webhook in github repo

## CICD on Jenkins
### Step 1: CI Job - Testing changes in Dev branch
- Description: Building a CI job with Github and local host
- Tick `Discard old builds`
- Set `Max # of builds to keep` as '3'
- Tick `Github project`
- Project URL 'your github url'
- Office 365 Connector:
    - Tick `Restrict where this project can be run`
    - Label Expression `sparta-ubuntu-node`
- Source Code Management
- Select Git
    - In Repositories:
        - Repository URL 'your repo URL'
        - Credentials: Add SSH key:
            - Add -> Jenkins -> Kind: 'SSH Username with private key' -> Give a description and Username -> Private key: `Enter directly` -> Enter contents of private key file (from git bash, in .ssh folder `cat <'private key file'>`) ->
    - In Branches to build:
        - Branch Specifier (blank for 'any'): */dev
- Build Triggers:
    - Tick `GitHub hook trigger for GITScm polling`
- Build Environment:
    - Tick `Provide Node & npm bin/ folder to PATH`
- Execute Shell:
    - Commands:
```
cd app
npm install
npm test
```
### Step 2: Merge - Merging Dev into Main branch
- 


### Step 1: Deploy App - Deploys 
- 