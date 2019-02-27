## Contributors
* [Joel Halford](https://github.com/JoelHalford): Front End
* [Fortune Osadolor](https://github.com/FortunexFortune): Back End
* [Ahmed Abid Ali](https://github.com/ahmedQAC): Back End
* [Taoheed Afolayan](https://github.com/Taoheed1): Testing
* [Ian Mallinson](https://github.com/imallinson): CI/CD

## Index
1. [Project Definition](#1-Project-Definition)

2. [Architecture](#2-Architecture)
     
3. [Containers](#3-Containers)
   * [NGINX](#NGINX)
   * [React Front End](#React-Front-End)
   * [Gateway](#Gateway)
   * [Accounts](#Accounts)
   * [Cohorts](#Cohorts)
   * [Form Submit](#Form-Submit)
   * [Data Retriver](#Data-Retriever)
   * [ActiveMQ](#ActiveMQ)
   * [Queue Consumer](#Queue-Consumer)
   * [MongoDB](#MongoDB)
     
4. [Testing](#4-Testing)
   * [Unit Testing](#Unit-Testing)
   * [Endpoint Testing](#Endpoint-Testing)
   * [Acceptance Testing](#Acceptance-Testing)

5. [How To Run](#5-How-To-Run)
   * [Prerequisites](#Prerequisites)
   * [Steps](#Steps)

6. [Continuous Integration](#6-Continuous-Integration)
   * [Docker](#Docker)
   * [Jenkins](#Jenkins)
   
7. [Repositories](#7-Repositories)

# 1. Project Definition
Trainees should be able to log in to submit a self-reflective feedback form on a weekly basis. Trainers should be able to log in and add trainees to specific cohorts to group them as well as view feedback submited and overall data on trainees and cohorts.

# 2. Architecture
![architecture-diagram](architecture-diagram.png)

Each white box in the diagram is a docker container

# 3. Containers
## NGINX
NGINX handles routing the user to the front end and routing the front end requests to the Gateway API. It also redirects all traffic to HTTPS to implement SSL for all connections.

## React
[ReactJS](https://reactjs.org/) has been used to build the front end for the app. It utilises a single page with routes to direct to the various views in the app.

## Gateway
The gateway receives all requests from the front end and redirects it to the correct microsevice.

## Accounts
This microservice deals with both account creation. Emails are validated and admin access is granted based on the email domain.

## Cohorts
This microservice deals with creating new cohorts to add trainees to.

## Form Submit
This microservice deals with persisting the feedback forms sent from the front end.

## Data Retriever
This microservice deals with getting the accounts, cohorts and feedback forms using a variety of criteria out of the database as well as adding trainees to a cohort.

## ActiveMQ
Queues requests from the APIs that are trying to persist data to the database.

## Queue Consumer
This microservice listens to the queue and sends any requests in the queue to the database.

## MongoDB
Stores all the data for the app.

# 4. Testing
## Unit Testing
[Mockito](https://site.mockito.org/) has been used to unit test the interactions with the database. These tests can be seen in the repos of the microservices.

## Endpoint Testing
[REST Assured](http://rest-assured.io/) has been used to test the rest endpoints for the microservices. These tests can be found in the [endpoint tests repo](https://github.com/imallinson/feedback-forms-endpoint-tests).

## Acceptance Testing
[Selinium](https://www.seleniumhq.org/) and [Cucumber](https://cucumber.io/) have been used to do tests for the acceptance criteria determined as part of the user stories for the app.

# 5. How To Run
## Prerequisites
* [Docker](https://hub.docker.com/search/?type=edition&offering=community)
* [Docker Compose](https://github.com/docker/compose/releases)
* A Shell Terminal

## Steps
1. Clone this repo
2. Run the install.sh script

# 6. Continuous Integration
## Docker
Having all the microservices in containers makes the app more portable. The containers being in a docker network allows the various microservices to communicate without being exposed to external access.

## Jenkins
Jenkins pipelines have been used to automate building, testing and deploying all the microservices whenever changes are made to the master Git branch.

# 7. Repositories
* [Front End](https://github.com/imallinson/feedback-forms-front)
* [Gateway API](https://github.com/imallinson/feedback-forms-gateway)
* [Accounts API](https://github.com/imallinson/feedback-forms-accounts)
* [Cohorts](https://github.com/imallinson/feedback-forms-cohorts)
* [Form Submit](https://github.com/imallinson/feedback-forms-submit)
* [Data Retriever](https://github.com/imallinson/feedback-forms-retriever)
* [Queue Consumer](https://github.com/imallinson/feedback-forms-consumer)
* [Endpoint Tests](https://github.com/imallinson/feedback-forms-endpoint-tests)
* [Acceptance Tests](https://github.com/imallinson/feedback-forms-acceptance-testing)
