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
