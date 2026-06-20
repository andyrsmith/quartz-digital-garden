---
title: Using Github Actions to Deploy Containerized App to EC2
date: 06/20/2026
tags:
  - github-actions
  - aws
links:
id: "202606200851"
---
# Using Github Actions to Deploy Containerized App to EC2

I created a simple python API to keep track of movie and shows that I want to watch, and books that I would like to read.  The API is not complete but I wanted to get it deployed on an AWS EC2 instances on push and merged to main.

This app is setup using a container and works using docker compose so when app is deploy to the EC2 instances it will git pull the latest changes and start the container using docker compose.
## Set Up the EC2 Instance

First step is setting up the EC2 instances. 

I created an micro ubuntu instances with 30 GB of hard drive space. Something small is fine for my needs.
Then created a new security group with inbound rules for ssh, and port 8000 (The port the App runs on).  8000 needs to allow any traffic, ssh can be restricted to my IPs that I will work from and Githubs IPs (For Github Actions).

After instances is created ssh into it using and perform system updates.

```
sudo apt-get update -y
sudo apt-get upgrade -y
```

Then install Docker Engine using the directions from the website.

https://docs.docker.com/engine/install/ubuntu/

Then clone the repository within the instance.  This way on deploy we will just pull down the latest on the instances.

## Set Up Github Actions

In Repo create a new directory .github/workflows, and create a file called ci-cd.yml file.

Set when we want to the actions to run.

```
name: Run Test and deploy to EC2
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  workflow_dispatch:
```

This block will tell the action to run on a push or when a pull request is created on the main branch.

Workflow dispatch is also included so I can trigger the job manually in Github if I want.

Now set up the test to run.

```
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Set up Docker compose
        run: |
          sudo apt-get update
          sudo apt-get install -y docker-compose
      - name: Build and run Docker containers
        run: |
          docker compose run --rm api pytest
      - name: Tear down Docker containers
        run: |
          docker-compose down
```

Using the actions/checkout@v2 to check out the repository, then run 3 separate commands.
First to update the container and install docker. Next run the test, and finally to bring down the container after it runs.

Now setup the deploy steps still nested under the jobs parameter.

```
  deploy:
    needs: test
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    environment: prod
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Deploy to EC2 & and run docker compose
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.EC2_HOST }}
          username: ${{ secrets.EC2_USER }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: |
            cd ~/MyStackAPI
            git pull origin main
            sudo docker compose -f docker-compose.prod.yml down
            sudo docker compose -f docker-compose.prod.yml up --build -d
```

With the line needs: test this will only run if test are successful, and if the branch is main. We don't want feature branches deploying code.

Then I use the appleboy/ssh-action@master to ssh into instances, get the latest code and restart docker compose.

With the parameters host, username, and key using variables those will need to be setup in github repo settings.

In settings in secrets and variables under Github actions create a new environment sercets.  This will prompt you to give it a environment name.  Use the same name as the environment parameter, which was prod. 

Then I created a variables 
EC2_HOST:  This is the ec2 instance public ip or public dns name.
EC2_USER: The user name of the instances.  For an ubuntu instances it is ubuntu. Other instances will have different user names.
EC2_KEY: This will be the value of the pem key that was created during the EC2 instances.

With all of that set on any push to main test runs and will deploy a new version of the application to my EC2 instances.

This is a simple way to automate the deployment of a containerized application to an EC2 instances. 

