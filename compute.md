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



Compute on AWS
When you consider what compute service to use for a specific use case, you should ensure that you are up to date on any new AWS service or feature releases. To review a high-level overview of the different AWS compute services AWS, see 
Compute on AWS - Compute for any workload
. 

AWS Lambda
For this weeks architecture, we have chosen AWS Lambda as the compute service due to it’s serverless nature and ability to support a web backend. Lambda is a compute service that provides serverless compute functions that run in response to events or triggers. When an event or trigger is detected, a Lambda function is spun up in its own secure and isolated runtime environment, which is called an execution environment. Lambda functions can run for up to 15 minutes. Any processes that need longer than 15 minutes to run should use other compute services on AWS for hosting. Each execution environment stays active for a period of time, and then it shuts down on its own. 

When you use Lambda, you are responsible only for your code, which can make it easier to optimize for operational efficiency and low operational overhead. Lambda manages the compute fleet, which offers a balance of memory, CPU, network, and other resources to run your code. Because Lambda manages these resources, you can’t log in to compute instances or customize the operating system on the provided runtimes. Lambda performs operational and administrative activities on your behalf, including managing capacity, monitoring, and logging your Lambda functions.If you need to manage your own compute resources, AWS has other compute services that can meet your needs. For example:

Amazon Elastic Compute Cloud (Amazon EC2) offers a wide range of EC2 instance types to choose from. With Amazon EC2, you can customize operating systems, settings for network and security, and the entire software stack. You are responsible for provisioning capacity, monitoring fleet health and performance, and using Availability Zones for fault tolerance.

AWS Elastic Beanstalk is a service that you can use to deploy and scale applications on Amazon EC2. You retain ownership and full control over the underlying EC2 instances.

Lambda can be used for virtually any application or backend that requires compute and that runs in under 15 minutes. Common use cases are web backends, Internet of Things (IoT) backends, mobile backends, file or data processing, stream or message processing, and more. Lambda is a good choice for use cases where the requirements include reducing operational overhead, optimizing for cost, or optimizing for performance efficiency. Lambda works well for these use cases because it’s a managed service and you only pay for what you use. There are no idling resources when working with AWS Lambda, which means that each Lambda function is highly performant and cost efficient. 

To gain a deeper understanding of Lambda, see 
AWS Lambda FAQs
.

To learn more about Lambda, see the 
AWS Lambda Developer Guide
 or the 
AWS Lambda Operator Guide
.

To learn more about architecting and best practices for Lambda, see 
Architecture and Best Practices
.

For a list of technical talks that cover Lambda, see 
AWS Lambda - Technical Talks
.

For a list of technical tutorials that use Lambda, see 
AWS Lambda - Workshops & Tutorials
.

Amazon API Gateway
After Morgan selected Lambda for the compute backend, she needed to find a way to expose the backend Lambda function. Amazon API Gateway integrates with Lambda, thus providing a way to expose the backend service without exposing to the open internet. This week’s customer might decide to add authentication to API Gateway to secure it further.

API Gateway is a fully managed service that makes it easier for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the front door for applications, so that the applications can access data, business logic, or functionality from your backend services. By using API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. API Gateway supports containerized and serverless workloads, as well as web applications.

API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including traffic management, CORS support, authorization and access control, throttling, monitoring, and API version management. API Gateway has no minimum fees or startup costs. You pay for the API calls you receive and the amount of data transferred out and, with the API Gateway tiered pricing model, you can reduce your cost as your API usage scales.

For more information about Amazon API Gateway, see 
Amazon API Gateway 
or 
Amazon API Gateway FAQs
.

Amazon EC2
Amazon EC2 is a service that provides resizable compute capacity in the cloud, which means that it provides virtual machines in the cloud. Amazon EC2 is a flexible service that offers multiple instance types, sizes, and pricing models to meet specific requirements. Because you can choose your operating system and configurations for your instance, you can configure Amazon EC2 to work with virtually any workload.

You can use Amazon EC2 when you want to run applications on AWS, but still want to retain control over the underlying infrastructure. Morgan didn’t choose Amazon EC2 as the compute service for this customer’s use case because of the operational overhead that Amazon EC2 requires. You have a lot of control over Amazon EC2, but that control also means that you will have overhead for managing the service. The customer had a straightforward use case and was willing to rewrite the code to use Lambda. The customer also had a spiky demand for their workload. Thus, choosing a service such as Lambda minimizes idling resources during low volume times, which can be more difficult to achieve with Amazon EC2.

For a beginner tutorial about Amazon EC2, see 
Get started with Amazon EC2 Linux instances
.

To gain a deeper understanding of Amazon EC2, see 
What is Amazon EC2?
 or 
Amazon EC2 FAQs
.

# AWS container services
Container management tools can be divided into three categories: registry, orchestration, and compute. AWS offers services that give you a secure place to store and manage your container images, orchestration that manages when and where your containers run, and flexible compute engines to power your containers. AWS can help manage your containers and their deployments for you, so you don't have to worry about the underlying infrastructure. No matter what you're building, AWS makes it easy and efficient to build with containers.

Container services were not chosen for this architecture because the customer did not want to integrate this technology into their stack. So, even though running a container on Amazon ECS using AWS Fargate as the compute platform would technically work it was not chosen because of other customer preferences.

# Amazon ECS
Amazon Elastic Container Service (Amazon ECS) is a fully managed container orchestration service that you can use to deploy, manage, and scale containerized applications. It integrates with the rest of the AWS Cloud to provide a secure and easy-to-use solution for running container workloads in the cloud or on premises. Key features of Amazon ECS:

Serverless by default with AWS Fargate: Fargate is built into Amazon ECS, and it reduces the time you need to spend on managing servers, handling capacity planning, or figuring out how to isolate container workloads for security. With Fargate, you define your application’s requirements and select Fargate as your launch type in the console or AWS Command Line Interface (AWS CLI). Then, Fargate takes care of all the scaling and infrastructure management that’s needed to run your containers.

Security and isolation by design: Amazon ECS natively integrates with the tools you already trust for security, identity, and management and governance. This can help you get to production quickly and successfully. You can assign granular permissions for each of your containers, giving you a high level of isolation when you build your applications. You can launch your containers with the security and compliance levels that you have come to expect from AWS.

Autonomous control plane operations: Amazon ECS is a fully-managed container orchestration service, with AWS configuration and operational best practices built-in—with no control plane, nodes, or add-ons for you to manage. It natively integrates with both AWS and third-party tools to make it easier for teams to focus on building the applications, not the environment.

# Amazon EKS
Amazon Elastic Kubernetes Service (Amazon EKS) is a managed service that you can use to run Kubernetes on AWS without needing to install, operate, and maintain your own Kubernetes control plane or nodes. Kubernetes is an open-source system for automating the deployment, scaling, and management of containerized applications. Amazon EKS offers the following features:

It runs and scales the Kubernetes control plane across multiple AWS Availability Zones to ensure high availability.

It also automatically scales control plane instances based on load, detects and replaces unhealthy control plane instances, and provides automated version updates and patching for them.

It is integrated with many AWS services to provide scalability and security for your applications, including the following capabilities:

Amazon Elastic Container Registry (Amazon ECR for container images).

Elastic Load Balancing for load distribution.

AWS Identity and Access Management (IAM) for authentication.

# Amazon Virtual Private Cloud (VPC) for isolation.

It runs up-to-date versions of Kubernetes, so you can use all of the existing plugins and tooling from the Kubernetes community. 

Applications that run on Amazon EKS are fully compatible with applications that run on any standard Kubernetes environment—it doesn’t matter whether they run in on-premises data centers or public clouds. This means that you can migrate any standard Kubernetes application to Amazon EKS with virtually no code modification.

# AWS Fargate
AWS Fargate is a technology that you can use with Amazon ECS to run containers without managing servers or clusters of EC2 instances. AWS Fargate reduces your need to provision, configure, or scale clusters of virtual machines to run containers. Thus, it also minimizes your need to choose server types, decide when to scale your clusters, or optimize cluster packing.

When you run your tasks and services with the Fargate launch type, you package your application in containers, specify the CPU and memory requirements, define networking and IAM policies, and launch the application. Each Fargate task has its own isolation boundary and doesn’t share the underlying kernel, CPU resources, memory resources, or elastic network interface with another task.

With Amazon ECS on AWS Fargate capacity providers, you can use both Fargate and Fargate Spot capacity with your Amazon ECS tasks. With Fargate Spot, you can run interruption-tolerant Amazon ECS tasks at a discounted rate, compared to the Fargate price. Fargate Spot runs tasks on spare compute capacity. When AWS needs the capacity back, your tasks will be interrupted with a 2-minute warning notice.


