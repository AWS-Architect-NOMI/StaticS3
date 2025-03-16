# StaticS3
Project 1: Static Website Hosting with AWS S3
Introduction

Hosting a static website using Amazon S3 is one of the simplest ways to leverage AWS cloud services. It provides a scalable and cost-effective way to serve static content like HTML, CSS, and JavaScript.

Architecture Overview

AWS S3: Stores website files.

AWS CloudFront: (Optional) Speeds up content delivery.

AWS Route 53: (Optional) Manages domain name resolution.

Step-by-Step Implementation

Create an S3 Bucket:

aws s3 mb s3://your-unique-bucket-name

Enable Static Website Hosting:

{
   "IndexDocument": { "Suffix": "index.html" }
}

Upload Your Website Files:

aws s3 cp index.html s3://your-unique-bucket-name/ --acl public-read

Set Public Access Policy:

{
   "Version": "2012-10-17",
   "Statement": [
      {
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-unique-bucket-name/*"
      }
   ]
}

Result

Your website is now hosted and accessible via the S3 endpoint.

Project 2: Serverless Web Application with AWS Lambda

Introduction

AWS Lambda allows you to build scalable serverless applications without managing backend servers.

Architecture Overview

AWS Lambda: Executes backend logic.

Amazon API Gateway: Routes HTTP requests.

DynamoDB: Stores data for the app.

Step-by-Step Implementation

Create a Lambda Function:

import json
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from AWS Lambda!')
    }

Deploy the Function:

aws lambda create-function --function-name myLambdaFunction --runtime python3.8 --role execution-role --handler lambda_function.lambda_handler --zip-file fileb://function.zip

Create an API Gateway to Trigger Lambda:

Go to API Gateway > Create API

Choose HTTP API and link it to Lambda.

Result

Your function is now accessible via an API endpoint.
