---  
title : "Create DynamoDB Table: PredictionHistory"  
date: "2025-08-12"  
weight : 4  
chapter : false  
pre : " <b> 4. </b> "  
---  

> **Objective**: Understand DynamoDB and create the `PredictionHistory` table to store image prediction history.  

---  

## Introduction to DynamoDB  

DynamoDB is AWS's serverless NoSQL database service, super fast, auto-scalable, and serverless. Perfect for storing data like prediction history in a serverless app.  

---  

## Create PredictionHistory table  

- Go to AWS Console → DynamoDB

  ![Find DynamoDB](/Workshop/images/4.create-dynamoDB/create-dynamoDB-1.png)  

  *Figure 1: Find DynamoDB services.*

- Continue select Table → Create Table to create new table

  ![Create Table](/Workshop/images/4.create-dynamoDB/create-dynamoDB-2.png)  

  *Figure 2: Click Create Table to start create new table.*

- Table name: `PredictionHistory`.  
- Partition key: `id` (Kiểu String).  
- You can skip Sort key (not needed).  

  ![Set up info](/Workshop/images/4.create-dynamoDB/create-dynamoDB-3.png)  

  *Figure 3: Set up attribute for table.*

- Keep other settings default and click Create table.  

  ![Create Table](/Workshop/images/4.create-dynamoDB/create-dynamoDB-4.png)  

  *Figure 4: Click Create Table to finish create table.*

---  

## Conclusion

Now your `PredictionHistory` table is ready to store data from Lambda functions. Next, we'll create Lambda functions to use this table!  

> **Ready to go?**  
> Move on to [Create Lambda function and API Gateway](/5-lambda-api-setup/)