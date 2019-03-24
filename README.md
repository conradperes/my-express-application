serverlessnodedynamodb

This is a Serverless Architecture Backend Rest project accessing a NOSQL DynamoDB table

You should type these commands to abble this function as a service in AWS, acessing Dynamo DB NOSQL table:

Creating environment: 

1- create the folder and entering on it: 

mkdir my-express-application && cd my-express-application

2-Initiate the node module to create the project: 

npm init -f

3-To install Express Framework (Web development framework) and serverless-http (Serverless architecture framework) to deploy on AWS Lambda you type on terminal: 

npm install --save express serverless-http

4- Install the dependencies aws-sdk and and body-parser: 

npm install --save aws-sdk body-parser

5-To deploy on AWS the entire STACK on AWS CloudFormations, assuring that the trigger will be API Gateway, and the Lambda function will be our index.js, and the content of template of the deployment descriptor is serverless.yml, type this: 

sls deploy

6-To test creating a record in table, make this request or in terminal or in postman, please notice that the the BASE_DOMAIN will be generated after deploy happend: 

export BASE_DOMAIN=https://mesx25omj0.execute-api.sa-east-1.amazonaws.com/dev/ 

curl -H "Content-Type: application/json" -X POST ${BASE_DOMAIN}/users -d '{"userId": "Conrad1", "name": "Conrad Marques Peres"}'

To test if user is really inside the DB: 

curl -H "Content-Type: application/json" -X GET ${BASE_DOMAIN}/users/Conrad1

Now let turn the things a little bit more intersting, let allow this project using DynamoDB locally and Node server also locally, to do this you must follow these steps:

7-The code index.js is ready to be adapt both for cloud use and local use.

8-To start the serverless offline server:

sls offline start

Test the application

9-To install the plugin serverless-dynamo-local to application, run this command: 

npm install --save-dev serverless-dynamodb-local

10-To run the install of DynamoDB locally on MAC: 

sls dynamodb install --localPath ./bin

11- To start the serverless locally now acessing the local DynamoDB: 

sls offline start

12-To create a user on Dynamo table locally: 

curl -H "Content-Type: application/json" -X POST http://localhost:3000/users -d '{"userId": "conrad777", "name": "Conrad Peres"}'

To retrieve the user: 

curl -H "Content-Type: application/json" -X GET http://localhost:3000/users/conrad777



And that's it! Now you can test you app locally, and then deploy to AWS to make your customers happy! :-)
