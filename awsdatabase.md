# Explore Databases on AWS
## UNDERSTANDING THE HISTORY BEHIND ENTERPRISE DATABASES
Choosing a database used to be a straightforward decision. There were only a few options to choose from. In the past, you likely considered a few vendors and then inevitably chose one for all of your applications.

Businesses often selected the database technology they were going to use, even before they fully understood their use case. Since the 1970s, the database most commonly selected by businesses was a relational database.

 ## WHAT IS A RELATIONAL DATABASE?
A relational database organizes data into tables. Data in one table can be linked to data in other tables to create relationships—hence, the relational part of the name.

A table stores data in rows and columns. A row, often called a record, contains all information about a specific entry. Columns describe attributes of that entry. Here’s an example of three tables in a relational database.
![image](https://github.com/gopal2812/awslearning/assets/39087216/28b006a6-8b51-4448-808a-62a3b81f9c0d)


This shows a table for books, a table for sales, and a table for authors. In the books table, each row includes the book ISBN, the title, the author, and the format. Each of these attributes is stored in its own column. The books table has something in common with the other two tables: the author attribute. That common column creates a relationship between the tables.

The tables, rows, columns, and relationships between them is referred to as a logical schema. With relational databases, a schema is fixed. Once the database is operational, it becomes difficult to change the schema. This requires most of the data modeling to be done upfront before the database is active.

# WHAT IS A RELATIONAL DATABASE MANAGEMENT SYSTEM?
A relational database management system (RDBMS) lets you create, update, and administer a relational database. Here are some common examples of relational database management systems:

MySQL

PostgresQL

Oracle

SQL server

Amazon Aurora

You communicate with most RDBMS by using Structured Query Language (SQL) queries. Here’s an example: SELECT * FROM table_name.

This query selects all of the data from a particular table. However, the real power of SQL queries is in creating more complex queries that let you pull data from several tables to piece together patterns and answers to business problems. For example, querying the sales table and the book table together to see sales in relation to an author’s books. This is made possible by a join, which we talk about next.

# THE BENEFITS OF USING A RELATIONAL DATABASE
There are many benefits to using a relational database. A few of them are listed here.

Joins: You can join tables, enabling you to better understand relationships between your data.

Reduced redundancy: You can store data in one table and reference it from other tables instead of saving the same data in different places.

Familiarity: Relational databases have been a popular choice since the 1970s. Due to this popularity, technical professionals often have familiarity and experience with this type of database.

Accuracy: Relational databases ensure that your data is persisted with high integrity and adheres to the ACID (atomicity, consistency, isolation, durability) principle.

## USE CASES FOR RELATIONAL DATABASES
Much of the world runs on relational databases. In fact, they’re at the core of many mission-critical applications, some of which you may use in your day to day life. Here are some common use cases for relational databases.Applications that have a solid schema that doesn’t change often, such as:

Lift and shift applications that lifts an app from on-premises and shifts it to the cloud, with little or no modifications.

Applications that need persistent storage that follows the ACID principle, such as:

Enterprise Resource Planning (ERP) applications

Customer Relationship Management (CRM) applications

Commerce and financial applications

CHOOSE BETWEEN UNMANAGED AND MANAGED DATABASES
If you want to run a relational database on AWS, you first need to select how you want to run it: the unmanaged way or the managed way.

The paradigm of managed versus unmanaged services is similar to the Shared Responsibility Model. The Shared Responsibility Model distinguishes between AWS’s and the customer’s security responsibility over a service. Similarly, managed versus unmanaged can be understood as a tradeoff between convenience and control.

On-Premises Database

Let’s say you operate a relational database on-premises (in your own data center). In this scenario, you are responsible for all aspects of operation, including the security and electricity of the data center, the management of the host machine, the management of the database on that host, as well as optimizing queries and managing customer data. You are responsible for absolutely everything, which means you have control over absolutely everything.

Unmanaged Database

![image](https://github.com/gopal2812/awslearning/assets/39087216/7577fe73-a512-4e53-9b57-6498cf26df81)

Now, let’s say you want to shift some of this work to AWS by running your relational database on Amazon EC2. If you host a database on Amazon EC2, AWS takes care of implementing and maintaining the physical infrastructure and hardware and installing the operating system of the EC2 instance. However, you’re still responsible for managing the EC2 instance, managing the database on that host, optimizing queries, and managing customer data.

This is what is often referred to as the unmanaged database option on AWS. AWS is responsible for and has control over the hardware and underlying infrastructure, and you are responsible and have control over management of the host and database.Managed Database


If you want to shift even more of the work to AWS, you can use a managed database service. These services provide the setup of both the EC2 instance and the database, and they provide systems for high availability, scalability, patching, and backups. However, you’re still responsible for database tuning, query optimization, and of course, ensuring that your customer data is secure. This provides you ultimate convenience, but you have the least amount of control compared to the two previous options.
![image](https://github.com/gopal2812/awslearning/assets/39087216/894291a4-0c7e-449d-bb77-5cbc651fcb24)


# Amazon Relational Database Service
What Is Amazon RDS?
Amazon RDS enables you to create and manage relational databases in the cloud without the operational burden of traditional database management. For example, if you sell healthcare equipment and your goal is to be the number-one seller in the Pacific Northwest, building out a database doesn’t directly help you achieve that goal though having a database is necessary to achieve the goal.   Amazon RDS helps you offload some of this unrelated work of creating and managing a database. You can focus on the tasks that differentiate your application, instead of infrastructure-related tasks such as provisioning, patching, scaling, and restoring.  Amazon RDS supports most of the popular relational database management systems, ranging from commercial options, open source options, and even an AWS-specific option. Here are the supported Amazon RDS engines. 

Commercial: Oracle, SQL Server

Open Source: MySQL, PostgreSQL, MariaDB

Cloud Native: Amazon Aurora


Note: The cloud native option, Amazon Aurora, is a MySQL and PostgreSQL-compatible database built for the cloud. It is more durable, more available, and provides faster performance than the Amazon RDS version of MySQL and PostgreSQL. To learn more about Amazon Aurora, view the 
Amazon Aurora FAQs
.  

# Understand DB Instances
Just like the databases that you would build and manage yourself, Amazon RDS is built off of compute and storage. The compute portion is called the DB (database) instance, which runs the database engine. Depending on the engine of the DB instance you choose, the engine will have different supported features and configurations. A DB instance can contain multiple databases with the same engine, and each database can contain multiple tables.  Underneath the DB instance is an EC2 instance. However, this instance is managed through the Amazon RDS console instead of the Amazon EC2 console. When you create your DB instance, you choose the instance type and size. Amazon RDS supports three instance families.

Standard, which include general-purpose instances

Memory Optimized, which are optimized for memory-intensive applications

Burstable Performance, which provides a baseline performance level, with the ability to burst to full CPU usage.


The DB instance you choose affects how much processing power and memory it has. Not all of the options are available to you, depending on the engine that you choose. You can find more information about the DB instance types in the resources section of this unit.  Much like a regular EC2 instance, the DB instance uses Amazon Elastic Block Store (EBS) volumes as its storage layer. You can choose between three types of EBS volume storage.

General purpose (SSD)

Provisioned IOPS (SSD)

Magnetic storage (not recommended)


# Work with Amazon RDS in an Amazon Virtual Private Cloud
When you create a DB instance, you select the Amazon Virtual Private Cloud (VPC) that your databases will live in. Then, you select the subnets that you want the DB instances to be placed in. This is referred to as a DB subnet group. To create a DB subnet group, you specify:

The Availability Zones (AZs) that include the subnets you want to add

The subnets in that AZ where your DB instance are placed

The subnets you add should be private so they don’t have a route to the internet gateway. This ensures your DB instance, and the cat data inside of it, can only be reached by the app backend.  Access to the DB instance can be further restricted by using network access control lists (ACLs) and security groups. With these firewalls, you can control, at a granular level, what type of traffic you want to allow into your database.  Using these controls provide layers of security for your infrastructure. It reinforces that only the backend instances have access to the database.

Use AWS Identity and Access Management (IAM) Policies to Secure Amazon RDS
Network ACLs and security groups allow you to dictate the flow of traffic. If you want to restrict what actions and resources your employees can access, you can use IAM policies.

# Back Up Your Data
You don’t want to lose any of that precious cat information. To take regular backups of your RDS instance, you can use: 

Automatic backups

Manual snapshots

Automatic Backups 

Automated backups are turned on by default. This backs up your entire DB instance (not just individual databases on the instance), and your transaction logs. When you create your DB instance, you set a backup window that is the period of time that automatic backups occur. Typically, you want to set these windows during a time when your database experiences little activity because it can cause increased latency and downtime.  

You can retain your automated backups between 0 and 35 days. You might ask yourself, “Why set automated backups for 0 days?” The 0 days setting actually disables automatic backups from happening. Keep in mind that if you set it to 0, it will also delete all existing automated backups. This is not ideal, as the benefit of having automated backups is having the ability to do point-in-time recovery.    


If you restore data from an automated backup, you have the ability to do point-in-time recovery. Point-in-time recovery creates a new DB instance using data restored from a specific point in time. This restoration method provides more granularity by restoring the full backup and rolling back transactions up to the specified time range.  

# Manual Snapshots 

If you want to keep your automated backups longer than 35 days, use manual snapshots. Manual snapshots are similar to taking EBS snapshots, except you manage them in the RDS console. These are backups that you can initiate at any time, that exist until you delete them.  

For example, to meet a compliance requirement that mandates you to keep database backups for a year, you would need to use manual snapshots to ensure those backups are retained for that period of time.  

If you restore data from a manual snapshot, it creates a new DB instance using the data from the snapshot.  


Which Backup Option Should I Use?
The answer, almost always, is both. Automated backups are beneficial for the point-in-time recovery. Manual snapshots allow you to retain backups for longer than 35 days.  

# Get Redundancy with Amazon RDS Multi-AZ
When you enable Amazon RDS Multi-AZ, Amazon RDS creates a redundant copy of your database in another AZ. You end up with two copies of your database: a primary copy in a subnet in one AZ and a standby copy in a subnet in a second AZ.   

The primary copy of your database provides access to your data so that applications can query and display that information.   

The data in the primary copy is synchronously replicated to the standby copy. The standby copy is not considered an active database, and does not get queried by applications.  

To improve availability, Amazon RDS Multi-AZ ensures that you have two copies of your database running and that one of them is in the primary role. If there’s an availability issue, such as the primary database losing connectivity, Amazon RDS triggers an automatic failover.  

When you create a DB instance, a domain name system (DNS) name is provided. AWS uses that DNS name to failover to the standby database. In an automatic failover, the standby database is promoted to the primary role and queries are redirected to the new primary database.   

To ensure that you don’t lose Multi-AZ configuration, a new standby database is created by either: 

Demoting the previous primary to standby if it’s still up and running

Or standing up a new standby DB instance

The reason you can select multiple subnets for an Amazon RDS database is because of the Multi-AZ configuration. You’ll want to ensure that you have used subnets in different AZs for your primary and standby copies.
Resources:
Certainly! When creating a database in Amazon RDS, you have the option to choose between Easy create and Standard create. Here's an explanation of the difference between these two options:

Easy create: This option is designed to simplify the database creation process by providing standard best practices for backups and high availability. When you choose Easy create, you accept the default settings recommended by Amazon RDS. It is a quick and straightforward way to set up a database without needing to make many configuration decisions.

Standard create: This option gives you more granular control over the features and settings of your database setup. With Standard create, you can customize various aspects such as storage, backup retention, maintenance windows, and more. It allows you to tailor the database configuration to meet your specific requirements and preferences.

In summary, Easy create is a simplified and recommended option that follows best practices, while Standard create provides more flexibility and control over the database configuration. The choice between the two options depends on your specific needs and level of customization required for your database setup.

# Q) Can you explain the difference between Easy create and Standard create options when creating a database in Amazon RDS?
Certainly! When creating a database in Amazon RDS, you have the option to choose between Easy create and Standard create. Here's an explanation of the difference between these two options:

Easy create: This option is designed to simplify the database creation process by providing standard best practices for backups and high availability. When you choose Easy create, you accept the default settings recommended by Amazon RDS. It is a quick and straightforward way to set up a database without needing to make many configuration decisions.

Standard create: This option gives you more granular control over the features and settings of your database setup. With Standard create, you can customize various aspects such as storage, backup retention, maintenance windows, and more. It allows you to tailor the database configuration to meet your specific requirements and preferences.

In summary, Easy create is a simplified and recommended option that follows best practices, while Standard create provides more flexibility and control over the database configuration. The choice between the two options depends on your specific needs and level of customization required for your database setup.

# What are the key components of Amazon RDS and how do they contribute to its functionality?
Amazon RDS (Relational Database Service) consists of several key components that contribute to its functionality. Here are the main components of Amazon RDS and their roles:

Database Engine: Amazon RDS supports various popular database engines such as MySQL, PostgreSQL, MariaDB, Microsoft SQL Server, and Amazon Aurora. The choice of the database engine depends on your specific requirements and preferences.

Database Instances: A database instance is similar to an EC2 instance and represents the computing resources allocated to run your database. You can choose the instance size and type based on your workload and performance needs.

Multi-AZ Deployment: Amazon RDS offers Multi-AZ deployment, which provides high availability and fault tolerance. In a Multi-AZ setup, a primary database instance is replicated to a standby instance in a different Availability Zone (AZ). If the primary instance fails, the standby instance is automatically promoted to become the primary, ensuring minimal downtime.

Backups and Snapshots: Amazon RDS provides automated backups, allowing you to easily restore your database to a specific point in time. You can also take manual snapshots for long-term retention or to create a new database instance.

Security and Access Control: Amazon RDS offers various security features, including network isolation, encryption at rest, and integration with AWS Identity and Access Management (IAM). You can control access to your database using IAM roles, database users, and security groups.

Monitoring and Metrics: Amazon RDS provides monitoring and metrics to help you track the performance and health of your database. You can use Amazon CloudWatch to monitor metrics such as CPU utilization, storage usage, and database connections.

Scaling and Performance: Amazon RDS allows you to scale your database resources up or down based on your needs. You can increase the instance size, allocate more storage, or enable auto-scaling to handle increased workloads efficiently.

These components work together to provide a managed and scalable database service in the AWS cloud. They simplify the setup, operation, and management of relational databases, allowing you to focus on your applications rather than the underlying infrastructure.

# Q) Can you explain the process of configuring RDS to launch a secondary DB instance in another subnet and AZ using Multi-AZ deployment?
Certainly! Configuring Amazon RDS to launch a secondary DB instance in another subnet and Availability Zone (AZ) using Multi-AZ deployment involves the following steps:

Enable Multi-AZ Deployment: When creating or modifying an Amazon RDS DB instance, you can enable Multi-AZ deployment. This can be done through the AWS Management Console, AWS CLI, or AWS SDKs. Enabling Multi-AZ deployment ensures that a standby DB instance is created in a different AZ.

Specify Subnets: During the configuration process, you need to specify the subnets where the primary and standby DB instances will be located. These subnets should be in different AZs to ensure high availability. Amazon RDS will automatically create the standby DB instance in the specified subnet.

Configure Security Groups: You need to configure the security groups for the primary and standby DB instances. Security groups control inbound and outbound traffic to the DB instances. Ensure that the necessary rules are set up to allow the required network connectivity.

Configure DB Instance Settings: Specify the DB instance identifier, instance class, storage, and other configuration settings for the primary DB instance. These settings determine the resources allocated to the primary DB instance.

Configure DB Instance Options: Set up additional options such as backup retention period, maintenance window, and parameter groups. These options allow you to customize the behavior and performance of the DB instance.

Review and Launch: Review the configuration settings and make any necessary adjustments. Once you are satisfied with the settings, launch the DB instance. Amazon RDS will create the primary and standby DB instances in the specified subnets and AZs.

Monitor and Manage: After the Multi-AZ deployment is complete, Amazon RDS automatically manages the replication of data between the primary and standby DB instances. It also handles failover in case of a primary instance failure. You can monitor the status and performance of the DB instances using Amazon CloudWatch and manage them through the AWS Management Console or APIs.

By following these steps, you can configure Amazon RDS to launch a secondary DB instance in another subnet and AZ using Multi-AZ deployment. This setup provides high availability and automatic failover, ensuring that your database remains accessible even in the event of an AZ-level failure.
