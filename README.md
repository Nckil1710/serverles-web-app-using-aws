# serverles-web-app-using-aws
This repository demonstrates a serverless web application architecture using AWS services like DynamoDB, AWS Lambda, and API Gateway for backend operations, and a simple frontend integrated with these services. 

`Steps to follow to make a serverless web`

For further Clarification you can refer this video from this link below (note there is no audio used in video for guidance).
https://drive.google.com/file/d/1ewgU0Uv8XJDsT_g24ouCQIovK4UbVZXU/view?usp=drive_link 

![Screenshot 2024-10-03 234603](https://github.com/user-attachments/assets/e8afb4a7-fc75-43f8-8087-1b5a7ddd77da)

1) **AWS Amplify**: A set of tools and services that simplify the development and deployment of scalable web and mobile applications on AWS, allowing developers to focus on building features rather than managing infrastructure.

2) **AWS API Gateway**: A fully managed service for creating, securing, and managing APIs at any scale, enabling easy access to backend services like AWS Lambda and other AWS resources.

3) **AWS Lambda**: A serverless, event-driven compute service that automatically runs your code in response to API calls or other events, eliminating the need to manage servers.

4) **DynamoDB**: A fully managed, serverless NoSQL database designed for high-performance applications, offering seamless scalability and low-latency data access.

Basically these are the steps we do in a short glimpse

    Deploy a static website to AWS Amplify.
    Create a serverless function using AWS Lambda.
    Build a REST API with API Gateway.
    Store data in a NoSQL database using DynamoDB.
    Manage permissions with IAM policies. Integrate your frontend code with the backend services.

**1.Deploy a static webiste to AWS Amplify**

    First we login to AWS Management Console and then search for Amplify and open it in a new tab.
    Now , we click on Deploy app and then select deploy without git since our code is in a local machine as index.html .
    After clicking next we give app a name and this stage a name of your wish and drag the file index.html which is converted to .zip file.
    Now we click save and deploy and website is deployed .we can access it using the link present there.
    
    It should be like this 
<img src="https://github.com/user-attachments/assets/343f9368-767b-4ade-a0c5-b37e7af2560c" width="500" alt="Description">


**Create a serverless function using AWS Lambda**

Step 1: Go to the AWS Management Console, navigate to Lambda.

Step 2: Create a new Lambda function:

    Choose "Author from scratch."
    Set the function name (e.g., studentManagementFunction).
    Choose Python, Node.js, or any runtime that matches your backend logic. Here i chose python 3.12

Step 3: Write your Lambda function logic:

    Integrate your code for operations like inserting, updating, viewing, and deleting students into DynamoDB. you can use the file i used as logic or your own code.

Step 4: Test the Lambda function with different payloads to ensure it is working as expected.

    #Here i used these test cases to test if my lambda function is working fine or not 
    

