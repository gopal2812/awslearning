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

# AWS Migration Hub offers several features that assist in the migration process:

IT Asset Inventory: Migration Hub acts as a single destination for storing IT asset inventory data. It allows you to import information about your on-premises servers and applications, creating a centralized repository of your existing IT assets.

Discovery Tools: Migration Hub provides options for performing deeper discovery of your infrastructure. You can use the AWS Discovery Agent or AWS Discovery Collector, which is an agentless approach specifically designed for VMware environments. These tools help gather detailed information about your servers and applications, including dependencies.

Network Visualization: Migration Hub offers a network visualization feature that helps accelerate planning by quickly identifying servers and their dependencies. It provides a visual representation of the network connections between servers, allowing you to understand the relationships and dependencies among your applications.

Strategy Recommendations: Based on the gathered data and network visualization, Migration Hub can provide strategy recommendations for your migration. These recommendations help you make informed decisions about the best approach for migrating your workloads to the AWS Cloud.

Orchestration: Migration Hub assists in orchestrating the migration process by providing tools and resources to help you plan and execute your migration. It offers features like migration groups, which allow you to group servers into applications, making it easier to manage and track the migration progress.

Migration Dashboard: Migration Hub provides a migration dashboard that shows the latest status and metrics for your rehost and replatform migrations. This dashboard helps you understand the progress of ongoing migrations and identify and troubleshoot any issues that may arise.

By utilizing these features, AWS Migration Hub simplifies and accelerates the migration process. It helps you create a data-driven inventory of your IT assets, visualize network connections, receive strategy recommendations, orchestrate migrations, and monitor the progress of your migration journey.
