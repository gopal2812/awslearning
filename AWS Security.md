# Security and the AWS Shared Responsibility Model
When you begin working with the AWS Cloud, managing security and compliance is a shared responsibility between AWS and you. To depict this shared responsibility, AWS created the shared responsibility model. This distinction of responsibility is commonly referred to as security of the cloud, versus security in the cloud.


# WHAT IS AWS RESPONSIBLE FOR?
AWS is responsible for security of the cloud. This means AWS is required to protect and secure the infrastructure that runs all the services offered in the AWS Cloud. AWS is responsible for:

Protecting and securing AWS Regions, Availability Zones, and data centers, down to the physical security of the buildings

Managing the hardware, software, and networking components that run AWS services, such as the physical server, host operating systems, virtualization layers, and AWS networking components

The level of responsibility AWS has depends on the service. AWS classifies services into three different categories. The following table provides information about each, as well as the AWS responsibility.

Category

# Examples of AWS Services in the Category

# AWS Responsibility

Infrastructure services

Compute services, such as Amazon Elastic Compute Cloud (Amazon EC2)

AWS manages the underlying infrastructure and foundation services.

# Container services

Services that require less management from the customer, such as Amazon Relational Database Service (Amazon RDS)

AWS manages the underlying infrastructure and foundation services, operating system, and application platform.

# Abstracted services

Services that require very little management from the customer, such as Amazon Simple Storage Service (Amazon S3)

AWS operates the infrastructure layer, operating system, and platforms, as well as server-side encryption and data protection.

Note
Container services refer to AWS abstracting application containers behind the scenes, not Docker container services. This enables AWS to move the responsibility of managing that platform away from customers.

# WHAT IS THE CUSTOMER RESPONSIBLE FOR?
You’re responsible for security in the cloud. When using any AWS service, you’re responsible for properly configuring the service and your applications, as well as ensuring your data is secure.The level of responsibility you have depends on the AWS service. Some services require you to perform all the necessary security configuration and management tasks, while other more abstracted services require you to only manage the data and control access to your resources. Using the three categories of AWS services, you can determine your level of responsibility for each AWS service you use.

Category

AWS Responsibility

Customer Responsibility

# Infrastructure services

AWS manages the infrastructure and foundation services.

You control the operating system and application platform, as well as encrypting, protecting, and managing customer data.

# Container services

AWS manages the infrastructure and foundation services, operating system, and application platform.

You are responsible for customer data, encrypting that data, and protecting it through network firewalls and backups.

# Abstracted services

AWS operates the infrastructure layer, operating system, and platforms, as well as server-side encryption and data protection.

You are responsible for managing customer data and protecting it through client-side encryption.

Due to the varying level of effort, it’s important to consider which AWS service you use and review the level of responsibility required to secure the service. It’s also important to review how the shared security model aligns with the security standards in your IT environment, as well as any applicable laws and regulations.It’s important to note that you maintain complete control of your data and are responsible for managing the security related to your content. Here are some examples of your responsibilities in context.

# Use IAM user instead of root user
Certainly! Fine-grained permissions refer to the ability to define and assign specific access levels and privileges to users or groups within an AWS account. In the context of IAM (Identity and Access Management) users, fine-grained permissions allow you to control precisely what actions a user can perform and what resources they can access within AWS.

# Here's how fine-grained permissions work with IAM users in AWS:

# Policy-based Access Control: IAM uses policies to define permissions. A policy is a JSON document that specifies the actions allowed or denied on specific AWS resources. You can attach policies to IAM users, groups, or roles to grant or restrict access to various services and resources.

# Actions and Resources: IAM policies allow you to specify the actions that a user can perform, such as creating an EC2 instance or accessing an S3 bucket. You can also define the resources on which these actions can be performed, such as specific EC2 instances or S3 buckets. This level of granularity ensures that users have access only to the resources they need for their tasks.

# Conditions: IAM policies can include conditions that further refine access control. For example, you can specify that a user can only perform certain actions within a specific time frame or from a particular IP address. Conditions provide additional flexibility in tailoring permissions to meet specific requirements.
Choosing a Region for AWS resources in accordance with data sovereignty regulations

Implementing data protection mechanisms, such as encryption and managing backups

Using access control to limit who has access to your data and AWS resources

# Understand the AWS Root User Credentials
The AWS root user has two sets of credentials associated with it. One set of credentials is the email address and password used to create the account. This allows you to access the AWS Management Console. The second set of credentials is called access keys, which allow you to make programmatic requests from the 
AWS Command Line Interface (AWS CLI) or AWS API
.  Access keys consist of two parts:

An access key ID, for example, A2lAl5EXAMPLE

A secret access key, for example, wJalrFE/KbEKxE

Similar to a username and password combination, you need both the access key ID and secret access key to authenticate your requests via the AWS CLI or AWS API. Access keys should be managed with the same security as an email address and password.


# IAM USER CREDENTIALS
An IAM user consists of a name and a set of credentials. When creating a user, you can choose to provide the user:

# Access to the AWS Management Console

Programmatic access to the AWS Command Line Interface (AWS CLI) and AWS Application Programming Interface (AWS API)

To access the AWS Management Console, provide the users with a user name and password. For programmatic access, AWS generates a set of access keys that can be used with the AWS CLI and AWS API. IAM user credentials are considered permanent, in that they stay with the user until there’s a forced rotation by admins.When you create an IAM user, you have the option to grant permissions directly at the user level.This can seem like a good idea if you have only one or a few users. However, as the number of users helping you build your solutions on AWS increases, it becomes more complicated to keep up with permissions. For example, if you have 3,000 users in your AWS account, administering access becomes challenging, and it’s impossible to get a top-level view of who can perform what actions on which resources.If only there were a way to group IAM users and attach permissions at the group level instead. Guess what: There is!

# WHAT IS AN IAM GROUP?
An IAM group is a collection of users. All users in the group inherit the permissions assigned to the group. This makes it easy to give permissions to multiple users at once. It’s a more convenient and scalable way of managing permissions for users in your AWS account. This is why using IAM groups is a best practice.If you have a an application that you’re trying to build and have multiple users in one account working on the application, you might decide to organize these users by job function. You might want IAM groups organized by developers, security, and admins. You would then place all of your IAM users in the respective group for their job function.This provides a better view to see who has what permissions within your organization and an easier way to scale as new people join, leave, and change roles in your organization.Consider the following examples.

A new developer joins your AWS account to help with your application. You simply create a new user and add them to the developer group, without having to think about which permissions they need.

A developer changes jobs and becomes a security engineer. Instead of editing the user’s permissions directly, you can instead remove them from the old group and add them to the new group that already has the correct level of access.

Keep in mind the following features of groups.

Groups can have many users.

Users can belong to many groups.

Groups cannot belong to groups.

The root user can perform all actions on all resources inside an AWS account by default. This is in contrast to creating new IAM users, new groups, or new roles. New IAM identities can perform no actions inside your AWS account by default until you explicitly grant them permission.The way you grant permissions in IAM is by using IAM policies.

# WHAT IS AN IAM POLICY?
To manage access and provide permissions to AWS services and resources, you create IAM policies and attach them to IAM users, groups, and roles. Whenever a user or role makes a request, AWS evaluates the policies associated with them. For example, if you have a developer inside the developers group who makes a request to an AWS service, AWS evaluates any policies attached to the developers group and any policies attached to the developer user to determine if the request should be allowed or denied.

IAM POLICY EXAMPLES
Most policies are stored in AWS as JSON documents with several policy elements. Take a look at the following example of what providing admin access through an IAM identity-based policy looks like.
```
{

"Version": "2012-10-17",    

     "Statement": [{        
          "Effect": "Allow",        

          "Action": "*",        

          "Resource": "*"     

     }]

}
```
In this policy, there are four major JSON elements: Version, Effect, Action, and Resource.

The Version element defines the version of the policy language. It specifies the language syntax rules that are needed by AWS to process a policy. To use all the available policy features, include "Version": "2012-10-17" before the "Statement" element in all your policies.

The Effect element specifies whether the statement will allow or deny access. In this policy, the Effect is "Allow", which means you’re providing access to a particular resource.

The Action element describes the type of action that should be allowed or denied. In the above policy, the action is "*". This is called a wildcard, and it is used to symbolize every action inside your AWS account.

The Resource element specifies the object or objects that the policy statement covers. In the policy example above, the resource is also the wildcard "*". This represents all resources inside your AWS console.

Putting all this information together, you have a policy that allows you to perform all actions on all resources inside your AWS account. This is what we refer to as an administrator policy.

Let’s look at another example of a more granular IAM policy.
```
{"Version": "2012-10-17",    

     "Statement": [{        

          "Effect": "Allow",        

          "Action": [            

               "iam: ChangePassword",            

               "iam: GetUser"            

               ]        

          "Resource": 

"arn:aws:iam::123456789012:user/${aws:username}"    

     }]

}
```
After looking at the JSON, you can see that this policy allows the IAM user to change their own IAM password (iam:ChangePassword) and get information about their own user (iam:GetUser). It only permits them to access their own credentials because the resource restricts access with the variable substitution ${aws:username}.

UNDERSTAND POLICY STRUCTURE
When creating a policy, it is required to have each of the following elements inside a policy statement.

Element

Description

Required

Example

Effect

Specifies whether the statement results in an allow or an explicit deny

✔

"Effect": "Deny"

Action

Describes the specific actions that will be allowed or denied

✔

"Action": "iam:CreateUser"

Resource

Specifies the object or objects that the statement covers

✔

"Resource": "arn:aws:iam::account-ID-without-hyphens:user/Bob"

Resources:


