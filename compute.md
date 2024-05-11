# Which AWS compute service would you choose to host the processing logic for automating the process of loading new items into an inventory database from an uploaded spreadsheet?
# If you have an application currently hosted in your on-premises data center that needs to be migrated to AWS, and you want to minimize the amount of refactoring needed, what compute option would you choose?
# In a scenario where you are planning to write a brand-new application using a microservices or service-oriented design, and you want to architect the application to scale up or down quickly and lower the risk of deploying new changes to production, which AWS compute service would you use?


When it comes to cost, there are some key differences between Amazon EC2 and AWS Lambda:

Amazon EC2:

EC2 charges you for the compute resources (instances) you provision, regardless of whether they are actively being used or not.
You are billed based on the instance type, the duration of usage (per hour or per second), and any additional resources attached to the instance (such as storage).
EC2 instances are typically billed on a pay-as-you-go basis, meaning you pay for the time the instances are running.
AWS Lambda:

Lambda charges you based on the number of requests and the duration of the code execution.
You are billed for the compute time consumed by your code, measured in milliseconds.
Lambda has a free tier that includes a certain number of requests and compute time per month, beyond which you are charged based on usage.
In summary, the key cost difference is that with EC2, you pay for the compute resources you provision, while with Lambda, you pay for the actual compute time your code consumes. Lambda's pay-per-use model can be more cost-effective for workloads with sporadic or low usage, as you only pay for the actual execution time. EC2 is more suitable for workloads that require dedicated instances or have consistent usage patterns.


The pay-per-use model of AWS Lambda makes it more cost-effective for workloads with sporadic or low usage due to the following reasons:

Granular Billing: AWS Lambda bills you based on the actual compute time your code consumes, measured in milliseconds. This means you only pay for the exact duration your code runs, rather than paying for idle time or unused resources.

No Idle Costs: With AWS Lambda, you don't incur any costs when your code is not running. Since Lambda functions are triggered by events or invocations, you are only billed when your code is actively executing in response to those triggers. This eliminates the need to provision and pay for idle compute resources.

Automatic Scaling: AWS Lambda automatically scales your code in response to incoming requests or events. It provisions the necessary compute resources to handle the workload, and you are only billed for the actual execution time. This dynamic scaling ensures that you have the right amount of resources to handle the workload efficiently without overpaying for unused capacity.

Free Tier: AWS Lambda offers a generous free tier that includes a certain number of requests and compute time per month. This allows you to experiment, develop, and run small workloads without incurring any costs. It's a great option for individuals or organizations with low usage requirements.

Overall, the pay-per-use model of AWS Lambda provides cost savings for workloads with sporadic or low usage by eliminating idle costs, offering granular billing, and providing automatic scaling capabilities. It allows you to optimize costs and pay only for the actual compute time your code consumes.


# Serverless and AWS Lambda
REMOVE THE UNDIFFERENTIATED HEAVY LIFTING

If you run your code on Amazon EC2, AWS is responsible for the physical hardware and you are responsible for the logical controls, such as guest operating system, security and patching, networking, security, and scaling.If you run your code in containers on Amazon ECS and Amazon EKS, AWS is responsible for more of the container management, such as deploying containers across EC2 instances and managing the container cluster. However, when running ECS and EKS on EC2, you are still responsible for maintaining the underlying EC2 instances.If you want to deploy your workloads and applications without having to manage any EC2 instances, you can do that on AWS with serverless compute.

GO SERVERLESS

Every definition of serverless mentions four aspects.

No servers to provision or manage.

Scales with usage.

You never pay for idle resources.

Availability and fault tolerance are built-in.

With serverless, spend time on the things that differentiate your application, rather than spending time on ensuring availability, scaling, and managing servers.AWS has several serverless compute options, including AWS Fargate and AWS Lambda.

EXPLORE SERVERLESS CONTAINERS WITH AWS FARGATE

Amazon ECS and Amazon EKS enable you to run your containers in two modes.

Amazon EC2 mode

AWS Fargate mode



AWS Fargate is a purpose-built serverless compute engine for containers. Fargate scales and manages the infrastructure, allowing developers to work on what they do best: application development.It achieves this by allocating the right amount of compute, eliminating the need to choose and handle EC2 Instances and cluster capacity and scaling. Fargate supports both Amazon ECS and Amazon EKS architecture and provides workload isolation and improved security by design.

AWS Fargate abstracts the EC2 instance so you’re not required to manage it. However, with AWS Fargate, you can use all the same ECS primitives, APIs, and AWS integrations. It natively integrates with AWS Identity and Access Management (IAM) and Amazon Virtual Private Cloud (VPC). Having native integration with Amazon VPC allows you to launch Fargate containers inside your network and control connectivity to your applications.

RUN YOUR CODE ON AWS LAMBDA

If you want to deploy your workloads and applications without having to manage any EC2 instances or containers, you can use AWS Lambda.AWS Lambda lets you run code without provisioning or managing servers or containers. You can run code for virtually any type of application or backend service, including data processing, real-time stream processing, machine learning, WebSockets, IoT backends, mobile backends, and web apps, like your corporate directory app!

AWS Lambda requires zero administration from the user. You upload your source code and Lambda takes care of everything required to run and scale your code with high availability. There are no servers to manage, bringing you continuous scaling with subsecond metering and consistent performance.

HOW LAMBDA WORKS

There are three primary components of a Lambda function: the trigger, code, and configuration.The code is source code, that describes what the Lambda function should run. This code can be authored in three ways.



You create the code from scratch.

You use a blueprint that AWS provides.

You use same code from the AWS Serverless Application Repository, a resource that contains sample applications, such as “hello world” code, Amazon Alexa Skill sample code, image resizing code, video encoding, and more.

When you create your Lambda function, you specify the runtime you want your code to run in. There are built-in runtimes such as Python, Node.js, Ruby, Go, Java, .NET Core, or you can implement your Lambda functions to run on a custom runtime.The configuration of a Lambda function consists of information that describes how the function should run. In the configuration, you specify network placement, environment variables, memory, invocation type, permission sets, and other configurations. To dive deeper into these configurations, check out the resources section of this unit.Triggers describe when the Lambda function should run. 

A trigger integrates your Lambda function with other AWS services, enabling you to run your Lambda function in response to certain API calls that occur in your AWS account. This makes you quicker to respond to events in your console without having to perform manual actions.All you need is the what, how, and when of a Lambda function to have functional compute capacity that runs only when you need it to.Amazon’s CTO, Werner Vogels, says, “No server is easier to manage than no server.” This quote summarizes the convenience you can have when running serverless solutions, like AWS Fargate and AWS Lambda. 

In the next unit, you apply all the information you’ve learned about Amazon EC2, Amazon ECS and Amazon EKS, and AWS Fargate and learn the use cases for each service.

AWS Lambda function handler

The AWS Lambda function handler is the method in your function code that processes events. When your function is invoked, Lambda runs the handler method. When the handler exits or returns a response, it becomes available to handle another event.You can use the following general syntax when creating a function handler in Python:

def handler_name(event, context):  ... return some_value

NAMING

The Lambda function handler name specified at the time you create a Lambda function is derived from the following:the name of the file in which the Lambda handler function is locatedthe name of the Python handler functionA function handler can be any name; however, the default on the Lambda console is lambda_function.lambda_handler. This name reflects the function name as lambda_handler, and the file where the handler code is stored in lambda_function.py.If you choose a different name for your function handler on the Lambda console, you must update the name on the Runtime settings pane.

BILLING GRANULARITY

AWS Lambda lets you run code without provisioning or managing servers, and you pay only for what you use. You are charged for the number of times your code is triggered (requests) and for the time your code executes, rounded up to the nearest 1ms (duration). AWS rounds up duration to the nearest millisecond with no minimum execution time. With this pricing, it can be very cost effective to run functions whose execution time is very low, such as functions with durations under 100ms or low latency APIs. For more information, see 
AWS News Blog
. 

SOURCE CODE

This video used a small amount of sample code illustrating a pattern for lazily generating assets using AWS Lambda and Amazon S3. If you’re looking to deploy a service to resize images to production, consider using the new release  
 Serverless Image Handler 
which is a robust solution to handle image manipulation and can be deployed via an AWS CloudFormation template.

You can find a tutorial on creating the AWS Lambda function as well as the code used in the AWS Lambda demo here: see 
AWS News Blog
. 

Resources:

External Site:
 AWS: Serverless

Coursera Course:
 Building Modern Python Applications on AWS

External Site:
 AWS: AWS Serverless resources

External Site:
 AWS: Building Applications with Serverless Architectures

External Site:
 AWS: Best practices for organizing larger serverless applications

External Site:
 AWS: Managing AWS Lambda functions

External Site:
 AWS: 10 Things Serverless Architects Should Know

External Site:
 AWS: AWS Alien Attack! A Serverless Adventure






