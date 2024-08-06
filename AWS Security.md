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

## Resources:


Role Based Access in AWS
Throughout these last few lessons, there have been sprinklings of IAM best practices. It’s helpful to have a brief summary of some of the most important IAM best practices you need to be familiar with before building out solutions on AWS.

## LOCK DOWN THE AWS ROOT USER


The root user is an all-powerful and all-knowing identity within your AWS account. If a malicious user were to gain control of root-user credentials, they would be able to access every resource within your account, including personal and billing information. To lock down the root user:

Don’t share the credentials associated with the root user.

Consider deleting the root user access keys.

Enable MFA on the root account.

## FOLLOW THE PRINCIPLE OF LEAST PRIVILEGE


Least privilege is a standard security principle that advises you to grant only the necessary permissions to do a particular job and nothing more. To implement least privilege for access control, start with the minimum set of permissions in an IAM policy and then grant additional permissions as necessary for a user, group, or role.

## USE IAM APPROPRIATELY

IAM is used to secure access to your AWS account and resources. It simply provides a way to create and manage users, groups, and roles to access resources within a single AWS account. IAM is not used for website authentication and authorization, such as providing users of a website with sign-in and sign-up functionality. IAM also does not support security controls for protecting operating systems and networks.

## USE IAM ROLES WHEN POSSIBLE


Maintaining roles is easier than maintaining users. When you assume a role, IAM dynamically provides temporary credentials that expire after a defined period of time, between 15 minutes and 36 hours. Users, on the other hand, have long-term credentials in the form of user name and password combinations or a set of access keys.User access keys only expire when you or the admin of your account rotates these keys. User login credentials expire if you have applied a password policy to your account that forces users to rotate their passwords.

## CONSIDER USING AN IDENTITY PROVIDER

If you decide to make your cat photo application into a business and begin to have more than a handful of people working on it, consider managing employee identity information through an identity provider (IdP). Using an IdP, whether it be an AWS service such as AWS IAM Identity Center (Successor to AWS Single Sign-On) or a third-party identity provider, provides you a single source of truth for all identities in your organization.You no longer have to create separate IAM users in AWS. You can instead use IAM roles to provide permissions to identities that are federated from your IdP.For example, you have an employee, Martha, that has access to multiple AWS accounts. Instead of creating and managing multiple IAM users named Martha in each of those AWS accounts, you can manage Martha in your company’s IdP. If Martha moves within the company or leaves the company, Martha can be updated in the IdP, rather than in every AWS account you have.

## CONSIDER AWS IAM IDENTITY CENTER


If you have an organization that spans many employees and multiple AWS accounts, you may want your employees to sign in with a single credential.AWS IAM Identity Center is an IdP that lets your users sign in to a user portal with a single set of credentials. It then provides them access to all their assigned accounts and applications in one central location.AWS IAM Identity Center is similar to IAM, in that it offers a directory where you can create users, organize them in groups, and set permissions across those groups, and grant access to AWS resources. However, AWS IAM Identity Center has some advantages over IAM. For example, if you’re using a third-party IdP, you can sync your users and groups to AWS IAM Identity Center.This removes the burden of having to re-create users that already exist elsewhere, and it enables you to manage those users from your IdP. More importantly, AWS IAM Identity Center separates the duties between your IdP and AWS, ensuring that your cloud access management is not inside or dependent on your IdP.

Q) How do IAM roles differ from IAM users and what are their main characteristics?
IAM roles in AWS differ from IAM users in several ways. Here are their main characteristics and differences:

# IAM Roles:

IAM roles are identities in AWS that can be assumed by someone or something who needs temporary access to AWS credentials.
IAM roles do not have login credentials like a username and password.
IAM roles have associated AWS credentials used to sign requests, which are programmatically acquired, temporary in nature, and automatically rotated.
IAM roles can be assumed by many different identities, such as AWS services or external identity providers.
IAM roles are commonly used for access between AWS services, where one service assumes a role to gain access to temporary credentials and send API calls to another service.
IAM roles are also used to grant access to existing identities from enterprise user directories, known as federated users.

# IAM Users:
IAM users are identities in AWS that represent a person or application that interacts with AWS services.
IAM users have login credentials, including a username and password, and can directly authenticate and access AWS resources.
IAM users have associated credentials, such as an access key ID and secret access key, which are used to sign requests.
IAM users can be assigned permissions through policies to control their access to AWS resources.
IAM users are typically used for long-term access and are associated with specific individuals or applications.

# Q) How can IAM roles be used to grant access to existing identities from enterprise user directories?
In summary, IAM roles are used for temporary access to AWS credentials, while IAM users are used for long-term access. IAM roles do not have login credentials and are assumed programmatically, while IAM users have login credentials and can directly authenticate with AWS.

IAM roles can be used to grant access to existing identities from enterprise user directories through a process called federated access. Here's how it works:

An identity provider (IdP) is set up in the enterprise user directory. This IdP could be an on-premises system or a cloud-based identity provider like Microsoft Azure Active Directory or Okta.

The enterprise user directory is configured to trust the AWS Security Token Service (STS) as a relying party.

When a user from the enterprise user directory needs access to AWS resources, they authenticate with the IdP using their existing credentials (username and password).

The IdP verifies the user's identity and generates a security token.

The user requests access to AWS resources by assuming an IAM role associated with their identity in the enterprise user directory.

The user presents the security token to the AWS STS, along with the ARN (Amazon Resource Name) of the IAM role they want to assume.

The AWS STS validates the security token and checks if the user is allowed to assume the specified IAM role.

If the validation is successful, the AWS STS issues temporary security credentials (access key, secret access key, and session token) for the user.

The user can then use these temporary credentials to access AWS resources based on the permissions assigned to the IAM role.

By leveraging IAM roles and federated access, organizations can avoid the need to create and manage individual IAM users for each employee in the enterprise user directory. This simplifies access management and allows users to use their existing credentials to access AWS resources securely.

Please note that the specific configuration steps may vary depending on the identity provider and AWS setup. It's recommended to refer to the AWS documentation for detailed instructions on setting up federated access with IAM roles.

# Q) Can you explain the process of assuming an IAM role and how temporary credentials are obtained for accessing AWS resources?

Certainly! Assuming an IAM role involves the process of obtaining temporary credentials that can be used to access AWS resources. Here's a step-by-step explanation of how it works:

An IAM role is created in AWS. This role defines the permissions and policies that determine what actions can be taken on AWS resources.

An entity, such as an IAM user or an AWS service, requests to assume the IAM role. This entity must have the necessary permissions to assume the role.

The entity sends a request to the AWS Security Token Service (STS) to assume the IAM role. The request includes the Amazon Resource Name (ARN) of the IAM role.

The AWS STS validates the request and checks if the entity is allowed to assume the specified IAM role. It verifies the identity of the entity and ensures that it has the necessary permissions.

If the validation is successful, the AWS STS generates temporary security credentials for the entity. These credentials consist of an access key, a secret access key, and a session token.

The AWS STS returns the temporary credentials to the entity.

The entity can then use these temporary credentials to make API calls to AWS services and access the resources allowed by the permissions assigned to the IAM role.

The temporary credentials have an expiration time, typically ranging from a few minutes to a few hours. Once the credentials expire, they can no longer be used to access AWS resources.

By assuming an IAM role, entities can obtain temporary credentials that provide access to AWS resources based on the permissions defined in the role. This allows for fine-grained access control and helps ensure the security of AWS resources.

It's important to note that the process of assuming an IAM role can be performed programmatically using AWS SDKs or through the AWS Management Console. The specific implementation details may vary depending on the programming language or the AWS service being used.

I hope this explanation helps! Let me know if you have any further questions.

![image](https://github.com/user-attachments/assets/1a4e48df-0758-4d96-926a-3367e426f50a)
![image](https://github.com/user-attachments/assets/cd25d120-bf54-4716-9b4a-be9cb7637077)
![image](https://github.com/user-attachments/assets/ba296eb8-ad6a-40e4-82df-6a5ee017561c)
![image](https://github.com/user-attachments/assets/2b38b64c-d75a-4be3-a340-e8b6664758d4)
![image](https://github.com/user-attachments/assets/7bb3fea0-f55e-4e96-b10f-b5ac68673cc1)





