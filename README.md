# serverles-web-app-using-aws
This repository demonstrates a serverless web application architecture using AWS services like DynamoDB, AWS Lambda, and API Gateway for backend operations, and a simple frontend integrated with these services. 

## Steps to follow to make a serverless web

For further Clarification you can refer this video from this link below (note there is no audio used in video for guidance).
> https://drive.google.com/file/d/1ewgU0Uv8XJDsT_g24ouCQIovK4UbVZXU/view?usp=drive_link 

<div align="center">
  <img src="https://github.com/user-attachments/assets/e8afb4a7-fc75-43f8-8087-1b5a7ddd77da" alt="method"/>
</div>

1) **AWS Amplify**: A set of tools and services that simplify the development and deployment of scalable web and mobile applications on AWS, allowing developers to focus on building features rather than managing infrastructure.

2) **AWS API Gateway**: A fully managed service for creating, securing, and managing APIs at any scale, enabling easy access to backend services like AWS Lambda and other AWS resources.

3) **AWS Lambda**: A serverless, event-driven compute service that automatically runs your code in response to API calls or other events, eliminating the need to manage servers.

4) **DynamoDB**: A fully managed, serverless NoSQL database designed for high-performance applications, offering seamless scalability and low-latency data access.

Basically these are the steps we do in a short glimpse

    1. Deploy a static website to AWS Amplify.
    2. Create a serverless function using AWS Lambda.
    3. Build a REST API with API Gateway.
    4. Store data in a NoSQL database using DynamoDB.
    5. Manage permissions with IAM policies. 
    6. Integrate your frontend code with the backend services.
    

> ## *Deploy a static webiste to AWS Amplify*

    First we login to AWS Management Console and then search for Amplify and open it in a new tab.
    Now , we click on Deploy app and then select deploy without git since our code is in a local machine as index.html .
<div align="center">
  <img src="https://github.com/user-attachments/assets/9458bcd3-3c7b-49fc-9fd9-6f69ccba3dbb" alt="method"/>
</div>

After clicking next we give app a name and this stage a name of your wish and drag the file index.html which is converted to .zip file.
<br>
<a href="index.html">HTML File link</a>

Now we click save and deploy and website is deployed .we can access it using the link present there.
<div align="center">
  <img src="https://github.com/user-attachments/assets/6630e627-130b-4e6f-bfa3-fa6301a609c9" alt="method"/>
</div>

    
It should be like this 
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/343f9368-767b-4ade-a0c5-b37e7af2560c" width="500" alt="Description">
</div>

> ## Create a serverless function using AWS Lambda

Step 1: Go to the AWS Management Console, navigate to Lambda.

Step 2: Create a new Lambda function:

        Choose "Author from scratch."
        Set the function name (e.g., studentManagementFunction).
        Choose Python, Node.js, or any runtime that matches your backend logic. Here i chose python 3.12

Step 3: Write your Lambda function logic:

    Integrate your code for operations like inserting, updating, viewing, and deleting students into DynamoDB. you can use the file i used as logic or your own code.
    here is the code file . In case you edit you lambda function always save and deploy it to update changes.


<div align="center">
    <a href="lambda.txt">Lambda Function Code</a>
  <img src="https://github.com/user-attachments/assets/199f5d7e-7b66-48ae-acaf-54a1d7fdb818" alt="lambda image"/>
</div>



Step 4: Test the Lambda function with different payloads to ensure it is working as expected.

    Here i used these test cases to test if my lambda function is working fine or not 
<a href="test.txt">Test Cases</a>

> ## *Build a REST API with API Gateway*


  Step 1: In the AWS Management Console, navigate to API Gateway.
  
  Step 2: Create a new API:
  
      Choose "REST API."
      Name it (e.g., StudentAPI).
  
  Step 3: Create resources and methods (e.g., /students, POST, GET, etc.) to handle requests from the frontend.we need four methods POST,GET,PUT and DELETE methods.
  
  <div align="center">
  <img src="https://github.com/user-attachments/assets/71712b00-6b5d-4717-8da4-a1e3cfc09e79" alt="method" width="500"/>
</div>

  
  Step 4: Integrate your Lambda function with the API Gateway:
  
      For each method (GET, POST, etc.), choose "Lambda Function" as the integration type and select the Lambda function you created.
      After Doing this click on enable CORS and click on all the methods you created and and save it.
<div align="center">
  <img src="https://github.com/user-attachments/assets/0d2099b5-46f1-4605-abf4-b2dec92d381b" alt="method" width="500"/>
</div>
  
  Step 5: Deploy the API by creating a new stage (e.g., web-stage).

  <div align="center">
  <img src="https://github.com/user-attachments/assets/2645c2de-bc9b-418a-94b6-16723358005b" alt="method" width="500"/>
</div>

  
  Step 6: Copy the API endpoint URL ***Invoke URL*** and use it in your frontend to interact with the backend.We will come back to this in integrating frontend with backend.
  
  <div align="center">
  <img src="https://github.com/user-attachments/assets/515d21ef-f63e-41bc-857f-61788cddfa0d" alt="method"/>
</div>


> ## *Store Data in a NoSQL Database Using DynamoDB*

Step 1: In the AWS Management Console, navigate to DynamoDB.

Step 2: Create a new table:

    Set the table name (e.g., student-table). 
    (NOTE: here i used student-table name in lambda function as well incase you name you db different be sure to update the name in lambda function).
    Use ID as the partition key and click create .

<div align="center">
  <img src="https://github.com/user-attachments/assets/9b52118f-6e08-4aa5-8c77-76a3d50af0f5" alt="method" width="500"/>
</div>


> ## *Manage Permissions with IAM Policies*
Configure your Lambda function to interact with DynamoDB:

Click on the table and in General Information and additional info copy your database arn .
<div align="center">
  <img src="https://github.com/user-attachments/assets/58a784bb-3986-40f7-8a67-f3a9570f177e" alt="method" />
</div>

Now Go to your lambda function and in configuration page click on permissions and click on the link in it .
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/a3b77025-5514-4f9c-913a-536276f1c0d3" alt="method" />
</div>

After opening the link ,click on Add Permissions and create a inline policy .select json format and paste this code.
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/e97f17f2-9ee2-4bc3-9f70-84297e14bbcd" alt="method" />
</div>
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/0ffad9e0-d5a4-4edc-b3a5-d2587d803d5e" alt="method" />
</div>


    {
    	"Version": "2012-10-17",
    	"Statement": [
    		{
    			"Sid": "VisualEditor0",
    			"Effect": "Allow",
    			"Action": [
    				"dynamodb:PutItem",
    				"dynamodb:DeleteItem",
    				"dynamodb:GetItem",
    				"dynamodb:Scan",
    				"dynamodb:Query",
    				"dynamodb:UpdateItem"
    			],
    			"Resource": "your database arn"
    		}
    	]
    }
Dont forget to give your database resource arn in resource part.

Click on next and name this policy as db-policy and create this policy .

**Now Comes the Testing of Lambda function with the test cases**. you can verify the test cases as the data is directly reflected in your Database.
Test through all testcases just in case.
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/60ea7499-84b8-4e94-96b8-e9f5497dc06e" alt="method"/>
</div>
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/fc4cb475-e474-4d44-bc21-3619c70a2bcd" alt="method"/>
</div>

You can they are reflected in database too.
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/cce9f111-362d-47eb-a2c8-d6449332adfd" alt="method"/>
</div>

> ## *Integrate your frontend code with the backend services.\*

In this final step, we will see everything we just built in action. We will update the front-end to be able to invoke the REST API with the help of our lambda function and receive data.

First, we open our index.html file and replace the invoke url you copied from rest api and place in every fetch operation in index.html .
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/981928ca-1114-4781-8ebd-7d5db1d4ed62" alt="method"/>
</div>


<a href="index.html">HTML File link</a>

After updating the index.html with invoke url we go the directory in which it is present and make this index.html into a zip .Incase your code has images,etc include those files too while making a zip file.
Now we go to management console and open Amplify and follow the same steps we used to create a web app in 1st step *Deploy a static webiste to AWS Amplify* .

Website will be like this
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/5e3cb75a-506f-40ef-903f-795adb32ec85" alt="method" width="500"/>
</div>

When we click on View Students i.e, Selection/GET Method
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/3674a295-254e-4b93-aac9-c59b68c5db0c" alt="method"/>
</div>

Adding a student detail i.e, Insertion/POST Method
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/ac4d62d7-cf67-412c-b021-845c55b5b50e" alt="method" width="500"/>
</div>
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/496b0cb1-38f7-443f-ae11-71a291015bf5" alt="method"/>
</div>

When editing a student details i.e, Updation/PUT Method
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/d94cb98b-cb4f-4231-8954-a4fce09fa6a4" alt="method" width="500"/>
</div>
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/59c2cc61-22b1-4ca2-9d0b-91889043d73d" alt="method"/>
</div>
<br>
Delete button to delete that student detail i.e, Deletion/DELETE Method
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/95b7a07d-3f81-44c4-a869-31b1411e2907" alt="method"/>
</div>
<br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/70eeb552-a392-4de4-96c5-2caf16a42963" alt="method" />
</div>
<br>
All these are also reflected in Database
<div align="center">
  <img src="https://github.com/user-attachments/assets/0a19207e-4654-4596-8e4e-efeccc8481e6" alt="method" />
</div>

***Reminder*** : Be Sure to delete the resources you create after your work is done .If this is kept running for a long time it may incur charges .



















    

