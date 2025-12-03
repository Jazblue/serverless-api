Serverless API with AWS CloudFormation
Overview

This project is a fully serverless CRUD API deployed entirely with AWS CloudFormation. It demonstrates end-to-end AWS skills, including Lambda, DynamoDB, API Gateway, IAM, and infrastructure-as-code.

Features

CRUD operations for items stored in DynamoDB.

Serverless compute using Python 3.10 Lambda functions.

REST API exposed via API Gateway.

Least-privilege IAM role for security.

Fully deployable with a single CloudFormation template.

Architecture

DynamoDB – stores items with id as the primary key.

Lambda Functions – handle API requests:

CreateItemLambda – adds new items

GetItemLambda – fetches a single item

GetAllItemsLambda – fetches all items

DeleteItemLambda – deletes items by ID

API Gateway – routes HTTP requests to Lambda functions.

IAM Role – allows Lambdas to access DynamoDB and CloudWatch logs.

CloudFormation – manages the entire infrastructure in a single YAML file.

Deployment

Use AWS CLI to deploy:

aws cloudformation deploy \
--stack-name serverless-api \
--template-file template.yml \
--capabilities CAPABILITY_NAMED_IAM \
--parameter-overrides EnvironmentName=dev

API Endpoints

Create Item

curl -X POST "https://<api-id>.execute-api.<region>.amazonaws.com/prod/items" \
-H "Content-Type: application/json" \
-d "{\"id\":\"1\",\"data\":\"Example item\"}"


Get Single Item

curl "https://<api-id>.execute-api.<region>.amazonaws.com/prod/items?id=1"


Get All Items

curl "https://<api-id>.execute-api.<region>.amazonaws.com/prod/items"


Delete Item

curl -X DELETE "https://<api-id>.execute-api.<region>.amazonaws.com/prod/items?id=1"

Skills Demonstrated

AWS Lambda & Python

DynamoDB CRUD operations

API Gateway integration

IAM roles & permissions

Infrastructure-as-code with CloudFormation

Serverless best practices

Notes

No AWS credentials are included in the repository.

The template is environment-aware (EnvironmentName parameter).

Can be extended with authentication, additional endpoints, or more AWS services.
