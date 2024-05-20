During this portion of the course, our goal is to introduce the concept of migration, and also introduce some of the concepts and preliminary resources that you might find helpful as you continue to learn about migrating to AWS.

One of the topics from this week is the 
# AWS shared responsibility model
 for security. The shared responsibility model describes a relationship where AWS is responsible for the security of the cloud, and you, as the customer, is responsible for the security in the cloud.

You also learned about a couple of approaches to migration that you can consider. One approach relates to the type of migration that you might be planning. Those types, which are laid out in the 
# 7 Rs of migration
, help you keep in mind the style of migration that you might need for your various applications.
Below we outline seven steps to a successful data migration.
Identify the data format, location, and sensitivity. ...
Planning for the size and scope of the project. ...
Backup all data. ...
Assess staff and migration tool. ...
Execution of the data migration plan. ...
Testing of final system. ...
Follow-up and maintenance of data migration plan.
The second approach is the 
three-phase migration process
: assess, mobilize, and migrate and modernize. This three-phase migration process was designed by AWS to help you approach your migration.

Closing this section, you learned about the 
# AWS Prescriptive Guidance
 page. On this page, you can find strategies, guides, and patterns to help accelerate your cloud migration. These resources were developed by AWS technology experts and the global community of AWS Partners.

# Migration Map
Creating a migration map before starting the migration process is crucial for a successful migration to the AWS Cloud. Here are a few reasons why it is important:

Clear Understanding of the Current State: By creating a migration map, you gain a clear understanding of your current on-premises architecture, including the applications, databases, and infrastructure components that need to be migrated. This helps you identify dependencies and potential challenges early on.

Efficient Planning: A migration map allows you to plan the migration process effectively. It helps you break down the migration into manageable tasks and prioritize them based on dependencies and criticality. This ensures a smooth and organized migration journey.

Choosing the Right AWS Services: With a migration map in hand, you can identify the AWS services that align with your on-premises components. This helps you make informed decisions about which AWS services to use for each component, ensuring a seamless transition to the cloud.

Resource Allocation: Creating a migration map helps you allocate the necessary resources, such as time, budget, and personnel, for the migration project. It allows you to estimate the effort required for each migration task and plan accordingly.

Risk Mitigation: A migration map helps you identify potential risks and challenges that may arise during the migration process. By having a clear plan in place, you can proactively address these risks and develop mitigation strategies to minimize any potential disruptions.

Communication and Collaboration: A migration map serves as a visual representation of the migration plan, making it easier to communicate and collaborate with stakeholders, including team members, management, and other departments involved in the migration process. It ensures everyone is on the same page and working towards a common goal.

Overall, creating a migration map provides structure, clarity, and direction to your migration project. It helps you avoid unnecessary delays, reduces risks, and increases the chances of a successful migration to the AWS Cloud.

Certainly! Let's consider an example of a migration map for an on-premises architecture that includes a web application, a relational database, and a file storage system. Here's how a migration map can help in choosing the right AWS services for each component:

Web Application:

Identify the current web application's requirements, such as the programming language, framework, and dependencies.
Research AWS services that support the identified requirements, such as AWS Elastic Beanstalk for hosting web applications or AWS Lambda for serverless applications.
Evaluate the scalability, performance, and deployment options of each service to determine the best fit for the web application.
Relational Database:

Determine the database engine and specific requirements of the relational database, such as data volume, performance, and availability.
Explore AWS services like Amazon RDS (Relational Database Service) that support the chosen database engine and provide managed database instances.
Consider factors like scalability, automated backups, and high availability features offered by the AWS service to ensure a smooth migration of the relational database.
File Storage System:

Assess the current file storage system's characteristics, such as file size, access patterns, and durability requirements.
Research AWS services like Amazon S3 (Simple Storage Service) or Amazon EFS (Elastic File System) that provide scalable and durable storage options.
Evaluate the pricing, performance, and integration capabilities of each service to select the most suitable option for the file storage system.
By creating a migration map, you can visually represent each component of your on-premises architecture and identify the specific AWS services that align with their requirements. This helps in making informed decisions and ensures that you choose the right AWS services for each component during the migration process.

When evaluating the cost implications of using AWS services for migrating on-premises components, consider the following factors:

Pricing Models: Understand the pricing models of the AWS services you plan to use. AWS offers various pricing options, such as pay-as-you-go, reserved instances, and spot instances. Evaluate which pricing model aligns best with your migration needs and budget.

Instance Types: Consider the different instance types available for the AWS services you are considering. Each instance type has different performance characteristics and pricing. Choose the instance type that meets the requirements of your on-premises component while optimizing costs.

Storage Options: Evaluate the storage options provided by AWS services. Consider factors such as storage capacity, performance, and pricing. Choose the storage option that aligns with the storage requirements of your on-premises component while considering cost-efficiency.

Data Transfer Costs: Assess the data transfer costs associated with migrating your on-premises data to AWS. Consider factors such as the volume of data to be transferred and the pricing structure for data transfer. Optimize data transfer costs by utilizing AWS services that offer free or reduced-cost data transfer options.

Additional Costs: Consider any additional costs associated with the AWS services you plan to use. This may include costs for data storage, data transfer, load balancing, monitoring, and other services. Evaluate these additional costs to ensure they fit within your budget.

Cost Optimization Tools: Leverage AWS cost optimization tools and services, such as AWS Cost Explorer and AWS Trusted Advisor, to analyze and optimize your costs. These tools provide insights into cost trends, recommendations for cost savings, and help you monitor and manage your AWS spending.

Long-Term Cost Planning: Consider the long-term cost implications of using AWS services. Evaluate factors such as scalability, future growth, and potential cost savings through AWS services like auto-scaling and reserved instances. Plan for long-term cost optimization and ensure that the chosen AWS services align with your future needs.

Remember, the cost implications may vary depending on the specific AWS services and on-premises components you are migrating. It's important to carefully evaluate the cost factors and leverage AWS cost management tools to optimize your costs throughout the migration process and beyond.
![image](https://github.com/gopal2812/awslearning/assets/39087216/ac345930-ccd9-466e-bfee-2d6ec066f383)

# "Migrating to the AWS Cloud," you will learn about the assess phase of migration and two useful tools within AWS: AWS Migration Evaluator and AWS Migration Hub.

AWS Migration Evaluator is a migration assessment service that helps create a business case for AWS Cloud planning and migration. It provides a baseline of your organization's current infrastructure and projects AWS costs based on on-premises provisioning and utilization. It also offers features like inventory discovery, quick insights assessment, and migration expertise to aid in assessing your migrations.

AWS Migration Hub is a tool that acts as a single destination for storing IT asset inventory data and tracking migrations to any AWS Region. It helps make the case for cloud within your organization, creates a data-driven inventory of existing IT assets, and provides network visualization, strategy recommendations, orchestration, and a migration dashboard.

These tools can assist you in assessing your environment and migration needs, and we will dive deeper into them later in the course.

#AWS Migration Evaluator has several features that aid in assessing migrations:

Inventory Discovery: Even if you don't have existing inventory and resource utilization data, the Migration Evaluator agentless collector can provide visibility by deploying it on-premises. It leverages read-only access to various infrastructure components like VMware, Hyper-V, Windows, Linux, Active Directory, and SQL Server to gather data.

Migration Evaluator Quick Insights: This feature provides a pre-migration assessment that gives both business and technical stakeholders visibility into the projected costs of running on-premises workloads in the AWS Cloud. It generates a one-page summary highlighting estimated savings to rehost at AWS, with cost breakdowns by infrastructure and software licenses. Detailed per-server and per-SQL-Server data is also available for a more technical audience.

AWS Migration Expertise: If your organization needs additional insights after receiving the Migration Evaluator Quick Insights assessment, you can request a Migration Evaluator business case. This feature includes a team of solutions architects who understand your migration objectives and use that data to narrow down the best-suited migration patterns. The results are captured in a business case that aligns business and technology stakeholders and provides prescriptive next steps in the migration journey.

These features help assess migrations by providing visibility into current infrastructure, projecting costs for rehosting on AWS, and offering recommendations for migration patterns. They enable stakeholders to make informed decisions and align business and technology goals during the migration process.

# The Migration Evaluator agentless collector is a tool deployed on-premises that gathers data from various infrastructure components without requiring any installation or modification of those components. Here's how it works:

Read-only Access: The agentless collector leverages read-only access to infrastructure components such as VMware, Hyper-V, Windows, Linux, Active Directory, and SQL Server. It does not make any changes or modifications to these components, ensuring the integrity and security of your existing infrastructure.

Data Collection: The collector collects data by scanning and analyzing the infrastructure components. It gathers information about the inventory, resource utilization, and configuration settings of these components.

Visibility: By accessing this data, the agentless collector provides visibility into your existing infrastructure. It helps create a baseline of what your organization is running, including details about servers, applications, databases, and other resources.

Accuracy: The collector aims to provide a high level of accuracy in data collection. It ensures that the gathered information reflects the current state of your infrastructure, enabling more precise assessments and cost projections.

Overall, the Migration Evaluator agentless collector offers a non-intrusive way to gather data from various infrastructure components, providing visibility into your existing environment and supporting accurate assessments for migration planning.


# The AWS Migration Expertise feature within AWS Migration Evaluator helps in narrowing down the best-suited migration patterns by leveraging a team of solutions architects who understand your migration objectives. Here's how it works:

Migration Objective: The AWS Migration Expertise team works with you to understand your specific migration objectives. This could include goals such as exiting a data center, changing software-licensing strategies, or optimizing infrastructure costs.

Data Analysis: Based on the migration objectives, the team analyzes the data collected by the Migration Evaluator tool. This data includes information about your existing infrastructure, resource utilization, and configuration settings.

Migration Patterns: Using their expertise and knowledge of AWS services, the team identifies a subset of migration patterns that are best-suited to your specific objectives. Migration patterns refer to the recommended approaches and strategies for migrating different types of workloads to the AWS Cloud.

Business Case: The results of the analysis and the identified migration patterns are captured in a Migration Evaluator business case. This business case helps align business and technology stakeholders by providing a clear understanding of the recommended migration approach and its benefits.

By leveraging AWS Migration Expertise, you can benefit from the knowledge and experience of solutions architects who can guide you in selecting the most appropriate migration patterns for your specific migration objectives. This helps ensure that your migration journey is aligned with your goals and maximizes the benefits of migrating to the AWS Cloud.
# The AWS Agentless Discovery Connector is a VMware appliance that collects information about VMware virtual machines. It is installed as a virtual machine (VM) in your VMware vCenter server environment using an open virtualization archive file (OVA).

Once installed, the Discovery Connector connects to the vCenter server and collects data about all the virtual machines and hosts managed by that specific vCenter. It securely sends the collected data to the AWS Application Discovery Service. This allows you to gather detailed information about your VMware virtual machines, which can be used for migration planning and tracking purposes.

The AWS Agentless Discovery Connector is specifically designed for VMware environments and helps minimize the time required for the initial infrastructure assessment of your on-premises environment.
# AWS Migration Hub offers several features that assist in the migration process:

IT Asset Inventory: Migration Hub acts as a single destination for storing IT asset inventory data. It allows you to import information about your on-premises servers and applications, creating a centralized repository of your existing IT assets.

Discovery Tools: Migration Hub provides options for performing deeper discovery of your infrastructure. You can use the AWS Discovery Agent or AWS Discovery Collector, which is an agentless approach specifically designed for VMware environments. These tools help gather detailed information about your servers and applications, including dependencies.

Network Visualization: Migration Hub offers a network visualization feature that helps accelerate planning by quickly identifying servers and their dependencies. It provides a visual representation of the network connections between servers, allowing you to understand the relationships and dependencies among your applications.

Strategy Recommendations: Based on the gathered data and network visualization, Migration Hub can provide strategy recommendations for your migration. These recommendations help you make informed decisions about the best approach for migrating your workloads to the AWS Cloud.

Orchestration: Migration Hub assists in orchestrating the migration process by providing tools and resources to help you plan and execute your migration. It offers features like migration groups, which allow you to group servers into applications, making it easier to manage and track the migration progress.

Migration Dashboard: Migration Hub provides a migration dashboard that shows the latest status and metrics for your rehost and replatform migrations. This dashboard helps you understand the progress of ongoing migrations and identify and troubleshoot any issues that may arise.

By utilizing these features, AWS Migration Hub simplifies and accelerates the migration process. It helps you create a data-driven inventory of your IT assets, visualize network connections, receive strategy recommendations, orchestrate migrations, and monitor the progress of your migration journey.

# What are some examples of server data that can be included in the CSV template for Migration Hub import?

When populating the CSV template for Migration Hub import, you can include various server data to gather information about your on-premises servers and applications. Some examples of server data that can be included in the CSV template are:

Server name or hostname
IP address
Operating system
CPU specifications (e.g., number of cores, clock speed)
Memory (RAM) size
Storage capacity
Network configuration
Application dependencies
Utilization data (e.g., CPU usage, memory usage)
Application version
Including these details in the CSV template will provide Migration Hub with the necessary information to plan and track the migration of your servers and applications to the AWS Cloud.

# The Migration Hub import tool and the AWS Application Discovery Service are two components that work together to facilitate the migration process. Here's how they are related:

Migration Hub import: Migration Hub import is a tool that allows you to import information about your on-premises servers and applications into the AWS Migration Hub. It provides a structured format (CSV template) for organizing and uploading the existing data. This tool helps you gather information and track the status of application migrations.

AWS Application Discovery Service: The AWS Application Discovery Service is a service that helps you plan and execute your migration to the AWS Cloud. It collects data about your on-premises servers, applications, and their dependencies. The AWS Application Discovery Service receives data from various sources, including the Migration Hub import tool.

The relationship between these two components is as follows:

Migration Hub import leverages the AWS Application Discovery Service to process and analyze the imported data. It uses the data gathered by the AWS Application Discovery Service to plan and track the migration of your servers and applications.

The AWS Application Discovery Service, in turn, receives data from multiple sources, including the Migration Hub import tool. It collects data from the Migration Hub import tool, as well as other tools like the AWS Agentless Discovery Connector and the AWS Application Discovery Agent.

By using both the Migration Hub import tool and the AWS Application Discovery Service, you can gather comprehensive information about your on-premises environment, plan your migration, and track the progress of your application migrations to the AWS Cloud.


# The process of migrating mainframe applications to the cloud involves several steps. Here is a high-level overview of the process:

Assess: This stage involves gaining insight into the existing mainframe application and identifying proposed changes. It helps highlight dependencies and create a plan to update the code to a more modern standard.

Refactor: In this stage, you have two options. The first option is to manually fix the code based on the suggestions provided during the assessment stage. The second option is to use the Mainframe Modernization service, which can automatically transform the code into agile Java services and web frameworks.

Re-platform: If you don't want to transform the application, you have the option to directly port the source code to the cloud without making any changes. This allows you to leverage the benefits of the cloud without modifying the application's code.

It's important to note that the specific steps and tools used in the migration process may vary depending on the organization and the specific requirements of the mainframe application. The AWS Mainframe Modernization service is designed to assist in this process by providing tools and guidance to help migrate mainframe workloads to the AWS Cloud.

# The AWS Mainframe Modernization service is designed to assist in migrating mainframe workloads to the cloud. Here's how it can help:

Assessment: The service provides insights into the proposed changes for your older application. It can identify dependencies and help you create a plan to update your code to a more modern standard.

Refactoring: The service offers suggestions for refactoring the code. You have the option to manually fix the code based on these suggestions or use the service to automatically transform the code into agile Java services and web frameworks.

Re-platforming: If you prefer not to transform the application, the service allows you to directly port the source code to the cloud without making any changes. This enables you to leverage the benefits of the cloud without modifying the application's code.

The AWS Mainframe Modernization service aims to simplify the migration process by providing tools and guidance tailored to mainframe workloads. It helps organizations modernize their applications and take advantage of the scalability, flexibility, and cost-efficiency of the AWS Cloud.

Remember, the specific steps and tools used in the migration process may vary depending on the organization and the specific requirements of the mainframe application. It's always recommended to refer to the official AWS documentation and consult with AWS experts for detailed guidance on using the Mainframe Modernization service.

# Can you explain the differences between manually fixing the code and using the automatic transformation option in the refactoring stage?
Certainly! In the refactoring stage of migrating mainframe applications to the cloud, you have two options: manually fixing the code or using the automatic transformation option. Here are the differences between the two:

Manual Fixing:

In this approach, you review the suggestions provided by the AWS Mainframe Modernization service and manually make the necessary changes to the code.
You have full control over the modifications and can tailor them to meet your specific requirements.
This option allows for more customization and fine-tuning of the code, but it may require more time and effort, especially for complex applications.
Automatic Transformation:

With the automatic transformation option, the AWS Mainframe Modernization service takes care of transforming the code into agile Java services and web frameworks.
The service uses automated tools and processes to convert the mainframe code into a more modern and cloud-compatible format.
This option can save time and effort, especially for large and complex applications, as the transformation is done automatically.
However, it's important to note that the automatic transformation may not always perfectly match the original code's behavior, and some manual adjustments may still be required.
The choice between manual fixing and automatic transformation depends on factors such as the complexity of the application, the desired level of customization, and the available resources. It's recommended to carefully evaluate the pros and cons of each approach and choose the one that best suits your specific migration requirements.

# ese services and tools included the 
Migration Readiness Assessment
, which includes dozens of questions for your team. These questions can help get everyone to a common place on how to view, plan, and perform your necessary migrations.

You also learned about two primary services during this time. The first service is the
 AWS Migration Evaluator
. You can use this service to work directly with the 
Migration Evaluator team
 to create a directional business case and provide additional insights for your migrations. The team will capture your objectives, and then use analytics to narrow down to the migration patterns that are best suited to your business needs. Also, keep in mind that you can 
browse through example data
 to get a better idea of what the Migration Evaluator can do for your organization.

The other service that you learned about is the 
AWS Migration Hub
. Migration Hub is one of the best resources you can have to help accelerate and simplify your migration to AWS. You can use Migration Hub to help make the case for cloud within your organization, create an inventory of assets, track your applications, and more. And though we introduced Migration Hub this week, you will continue to learn about it throughout the remainder of the course.

# Enable: These tools are designed to give users an environment in which they can create their architecture inside a standardized sandbox. One example is AWS Control Tower, which helps set up multiple AWS accounts with predefined rules and guidelines. It ensures that users follow best practices and helps prevent issues like turning off important services or deleting logs.

# Provision: These tools assist in provisioning resources and building out your architecture. CloudFormation is a popular tool in this category, allowing you to write infrastructure as code and deploy it. It helps standardize your architecture and enables easy auditing of the code before deployment. Another tool in this category is Service Catalog, which provides a vetted and standardized way for users to select and deploy resources.

# Operate: These tools help automate and control running architecture. AWS Systems Manager is a tool that simplifies the management of resources by providing an easy way to deploy, update, and make changes across multiple instances. CloudWatch is another tool that falls under this category, providing monitoring and logging capabilities to help you track the performance of your applications in the cloud.

These three categories of tools in AWS management and governance services enable users to create, provision, and operate their resources effectively in the AWS Cloud.

# Can you provide an example of how CloudFormation can be used to provision resources in a standardized way?
AWS Control Tower helps in enforcing standards and preventing issues during migration by providing a set of predefined rules and guidelines that users must follow. Here's how it works:

Standardized Environment: AWS Control Tower allows you to set up multiple AWS accounts with predefined guardrails. These guardrails ensure that users create their architecture within a standardized environment. By providing a consistent and controlled environment, Control Tower helps enforce standards across the organization.

Logging and Auditing: Control Tower automatically creates a logging and auditing account. This account keeps track of what is being built and provides visibility into the activities performed by users. It helps prevent issues like turning off important services or deleting logs, as these actions can be monitored and audited.

Best Practices: Control Tower includes best-practice guardrails that users can enable with just a few clicks. These guardrails are designed to prevent common mistakes and ensure that resources are created following AWS best practices. Users can choose to use the out-of-the-box best-practice guardrails or customize them to meet their specific requirements.

Compliance and Security: Control Tower helps enforce compliance and security standards during migration. It can check and ensure that resources, such as RDS databases, are encrypted. It also provides the ability to perform complex checks to meet specific compliance requirements.

By using AWS Control Tower, organizations can establish and enforce standards, prevent issues, and ensure that resources are created in a consistent and secure manner during the migration process. It simplifies the management and governance of AWS accounts, making it easier to maintain control and compliance across the organization.

# Q) Can you explain how AWS Systems Manager helps in managing resources across multiple instances?
Certainly! AWS Systems Manager helps in managing resources across multiple instances by providing a centralized and automated approach to managing and configuring those instances. Here's how it works:

Inventory and Configuration Management: AWS Systems Manager allows you to collect inventory and configuration data from your instances. It provides a detailed view of the software and hardware configurations, installed applications, and other system information. This helps you keep track of the resources across your instances and ensures they are properly configured.

Run Command: With AWS Systems Manager, you can execute commands or scripts on multiple instances simultaneously. This eliminates the need to manually log in to each instance and perform tasks individually. You can run commands to install software updates, execute maintenance tasks, or perform troubleshooting actions across a fleet of instances.

Patch Management: Systems Manager simplifies the process of managing software patches across your instances. It provides a Patch Manager feature that allows you to define patch baselines and automatically apply patches to instances based on those baselines. This helps keep your instances up to date with the latest security patches and reduces the risk of vulnerabilities.

Automation: AWS Systems Manager includes an Automation feature that enables you to create and execute workflows for common operational tasks. You can define a series of steps to be performed on multiple instances, such as creating snapshots, taking backups, or configuring security settings. This helps automate repetitive tasks and ensures consistency across your instances.

Parameter Store: Systems Manager includes a Parameter Store, which is a secure storage service for configuration data. You can store and manage configuration parameters, secrets, and other sensitive information centrally. This allows you to securely store and retrieve configuration values across your instances, making it easier to manage and update configurations.

Monitoring and Insights: Systems Manager integrates with other AWS services, such as CloudWatch, to provide monitoring and insights into your instances. You can collect and analyze performance metrics, view logs, and set up alarms to detect and respond to issues proactively.

By using AWS Systems Manager, you can efficiently manage and configure resources across multiple instances. It simplifies tasks such as inventory management, command execution, patch management, automation, and configuration management. This centralized approach helps streamline operations, improve efficiency, and ensure consistency across your instances in the AWS Cloud.


As part of your time with the mobilize phase of the migration process this week, you learned about reevaluating of migration plan based on the data that you obtain through the assess phase. You also moved another step closer to finalizing the plans for migrating your applications.

One of the services that we discuss is 
# AWS Application Discovery Service
, which can help you plan the migration of your various applications. You can use Application Discovery Service to view server utilization; map resource dependencies; and collect behavior, usage, and configuration data from your servers.

If you would like to view and work with the 
commands used to install the AWS Application Discovery Service Agent
 (Discovery Agent) during the demo, learning about the commands could help you better understand the service, how it operates, and how you might be able to use it.

Additionally, as you move closer to starting your actual migrations, you learned about two helpful tools that you can use to prepare your environments within AWS. The first tool is 
AWS Landing Zone
, which can help you save time by automating the setup of an environment by creating core accounts and resources. It also provides a baseline environment to help you get started with a multi-account architecture, identity and access management, governance, and more.

# AWS Control Tower
 is the other tool that you can use for this stage of preparation. AWS Control Tower provides a way to set up and govern secure, multi-account AWS environments, which are called landing zones. By using 
AWS Organizations
, AWS Control Tower helps to bring ongoing account management and governance, and also the implementation of best practices based on AWS experience.

Speaking of governance, it’s very important for you to use the available tools to help make your environments secure and compliant as you migrate. 
AWS Management and Governance
 offers many tools that can help with management and governance before and during your migration, and also with your ongoing usage and optimizations in AWS.

 ![image](https://github.com/gopal2812/awslearning/assets/39087216/cef08cd2-415b-4fa6-ac4b-be07193de228)

 # Summary

 During the migrate and modernize section, you mostly learned about tools that can primarily help you with the migration of your data. One of the first introduced was the 
AWS Database Migration Service
, which helps to migrate databases to AWS quickly and securely. The service also keeps the source database operational during the migration, helping to minimize downtime and impact to resources dependent on the databases.

From there, you learned about four services that help to manage and move data between AWS and your on-premises environments. The first service that you learned about is 
AWS DataSync
, which is a secure service that automates moving data between locations. DataSync can copy data between various storage systems and types, and AWS.

The second service that you learned about is 
AWS Storage Gateway
, a hybrid cloud storage service that gives on-premises access to virtually unlimited cloud storage. Storage Gateway provides a standard set of storage protocols, the use of AWS storage without needing to rewrite your existing applications, and a suite of gateway types for you to use (depending on your needs).

Another service in this realm is 
AWS Direct Connect
. Direct Connect links your internal network to an AWS Direct Connect location over a standard Ethernet fiber-optic cable, which connects your router to a Direct Connect router. By using Direct Connect, you can interface directly with public AWS services or to Amazon Virtual Private Cloud (Amazon VPC)—and thus bypass internet service providers in your network path.

The fourth service suite is the 
AWS Snow Family
, which includes AWS Snowcone, AWS Snowball, and AWS Snowmobile. All AWS Snow Family services are helpful if you need to quickly move large amounts of data to AWS, and they also provide options for preprocessing the data before it’s migrated. The Snowcone and Snowball devices were shown directly in the videos, and 
Snowmobile is also an option
 if you need to move petabytes of data as quickly as possible.

To close out our migration course, we wanted to make sure that you learned about another tool that can help you as you continue to develop your AWS skills. 
AWS Skill Builder
 is a great location where you can find hundreds of hours of no-charge content, and links to various training and certification resources.



