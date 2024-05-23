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

## Introduction to Amazon DynamoDB
# What Is Amazon DynamoDB?
Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. DynamoDB lets you offload the administrative burdens of operating and scaling a distributed database so that you don't have to worry about hardware provisioning, setup and configuration, replication, software patching, or cluster scaling. 

With DynamoDB, you can create database tables that can store and retrieve any amount of data and serve any level of request traffic. You can scale up or scale down your tables' throughput capacity without downtime or performance degradation. You can use the AWS Management Console to monitor resource utilization and performance metrics.

DynamoDB automatically spreads the data and traffic for your tables over a sufficient number of servers to handle your throughput and storage requirements, while maintaining consistent and fast performance. All of your data is stored on solid-state disks (SSDs) and is automatically replicated across multiple Availability Zones in an AWS Region, providing built-in high availability and data durability. 

# Core Components of Amazon DynamoDB
In DynamoDB, tables, items, and attributes are the core components that you work with. A table is a collection of items, and each item is a collection of attributes. DynamoDB uses primary keys to uniquely identify each item in a table and secondary indexes to provide more querying flexibility. 

The following are the basic DynamoDB components:

Tables – Similar to other database systems, DynamoDB stores data in tables. A table is a collection of data. For example, see the example table called People that you could use to store personal contact information about friends, family, or anyone else of interest. You could also have a Cars table to store information about vehicles that people drive.

Items – Each table contains zero or more items. An item is a group of attributes that is uniquely identifiable among all of the other items. In a People table, each item represents a person. For a Cars table, each item represents one vehicle. Items in DynamoDB are similar in many ways to rows, records, or tuples in other database systems. In DynamoDB, there is no limit to the number of items you can store in a table.

Attributes – Each item is composed of one or more attributes. An attribute is a fundamental data element, something that does not need to be broken down any further. For example, an item in a People table contains attributes called PersonID, LastName, FirstName, and so on. For a Department table, an item might have attributes such as DepartmentID, Name, Manager, and so on. Attributes in DynamoDB are similar in many ways to fields or columns in other database systems.

# Security with Amazon DynamoDB
DynamoDB also offers encryption at rest, which eliminates the operational burden and complexity involved in protecting sensitive data. For more information, see 
DynamoDB Encryption at Rest
.

Below you can find additional resources for learning about Amazon DynamoDB:

Choose the Right AWS Database Service
AWS Database Services
AWS has a variety of different database options for different use cases. Use the table below to get a quick look at the AWS database portfolio.  

Database Type   Use Cases                                            AWS Service

Relational     Traditional applications, ERP, CRM, e-commerce      Amazon RDS, Amazon Aurora, Amazon Redshift

Key-value      High-traffic web apps, e-commerce systems, gaming applications   Amazon DynamoDB

In-memory      Caching, session management, gaming leaderboards, geospatial applications  Amazon ElastiCache for Memcached, Amazon ElastiCache for Redis

Document       Content management, catalogs, user profiles    Amazon DocumentDB (with MongoDB compatibility)

Wide column    High-scale industrial apps for equipment maintenance, fleet management, and route optimization   Amazon Keyspaces (for Apache Cassandra)

Graph          Fraud detection, social networking, recommendation engines        Amazon Neptune

Time series    IoT applications, DevOps, industrial telemetry                    Amazon Timestream

Ledger         Systems of record, supply chain, registrations, banking transactions  Amazon QLDB

Breaking Up Applications and Databases
As the industry changes, applications and databases change too. Today, with larger applications, you no longer see just one database supporting it. Instead, these applications are being broken into smaller services, each with their own purpose-built database supporting it.   

This shift removes the idea of a one-size-fits-all database and replaces it with a complimentary database strategy. You can give each database the appropriate functionality, performance, and scale that the workload requires. 

![image](https://github.com/gopal2812/awslearning/assets/39087216/5bb85031-6a1b-482b-aa22-f43ef5e8a45c)

# How does DynamoDB Streams capture and process item-level changes in a table?
DynamoDB Streams captures item-level changes in a table and processes them in the following way:

Enable DynamoDB Streams: First, you need to enable DynamoDB Streams for the table you want to capture changes for. This can be done through the AWS Management Console or by using the AWS SDKs or CLI.

Capture Changes: Once DynamoDB Streams is enabled, it captures changes made to items in the table. These changes include both new and updated items, as well as deleted items.

Stream Records: DynamoDB Streams organizes the captured changes into ordered streams of records. Each record represents a single data modification event in the table.

Process the Stream: You can configure an application or service to process the stream of records from DynamoDB Streams. This can be done using AWS Lambda, which allows you to write code that automatically triggers in response to changes in the stream.

Handle the Records: When processing the stream, your application can access the records and perform various actions based on the changes. For example, you can update other systems or databases, trigger notifications, or perform analytics on the data.

Fault Tolerance: DynamoDB Streams ensures fault tolerance by automatically retrying failed records and maintaining the order of records within a shard.

By leveraging DynamoDB Streams, you can build real-time applications, perform data replication, maintain audit trails, and implement other use cases that require capturing and processing item-level changes in a DynamoDB table.

# Can you explain the difference between a local index and a global index in DynamoDB?
ertainly! In DynamoDB, there are two types of indexes: local indexes and global indexes. Here's an explanation of the difference between the two:

#Local Index:

A local index is an index that has the same partition key as the base table but a different sort key.
It is created at the time of table creation and cannot be added or modified later.
Local indexes are useful when you want to query the base table using different sort keys.
They provide an efficient way to access a subset of items in the table based on the partition key and a different sort key.
Local indexes have the same provisioned throughput as the base table.
Global Index:

A global index is an index that can have a different partition key and sort key than the base table.
It can be created at the time of table creation or added later.
Global indexes are useful when you want to query the table based on attributes other than the primary key.
They provide an efficient way to access items in the table based on different attributes.
Global indexes have their own provisioned throughput, which can be different from the base table.
They can be created in different AWS Regions, allowing for multi-region replication and improved availability.
In summary, local indexes are used to query the base table using a different sort key, while global indexes allow querying the table based on attributes other than the primary key and can be created in different AWS Regions. Both types of indexes provide efficient ways to access data in DynamoDB based on different criteria.


# When choosing between local indexes and global indexes in DynamoDB, there are several considerations to keep in mind. Here are some factors to consider:

Query Patterns: Consider the specific query patterns and access patterns of your application. Determine whether you need to query the table using a different sort key (local index) or access items based on attributes other than the primary key (global index).

Data Model: Evaluate your data model and understand the relationships between different attributes. Determine if a local index or a global index aligns better with your data model and the way you want to access and query the data.

Provisioned Throughput: Consider the provisioned throughput requirements for your application. Local indexes share the same provisioned throughput as the base table, while global indexes have their own provisioned throughput. Evaluate the read and write capacity units needed for each index type.

Scalability: Consider the scalability requirements of your application. Global indexes provide more scalability options as they can be created in different AWS Regions, allowing for multi-region replication and improved availability. Local indexes are limited to the same AWS Region as the base table.

Data Consistency: Evaluate the consistency requirements of your application. Local indexes provide strong consistency, meaning that the index is updated immediately after a write operation. Global indexes, by default, provide eventual consistency, where there might be a slight delay in updating the index after a write operation.

Table Size and Cost: Consider the impact on table size and cost. Local indexes increase the storage requirements of the table as they store additional index data. Global indexes also increase storage requirements and have their own provisioned throughput, which can affect the cost of your DynamoDB usage.

Index Creation and Modification: Determine whether you need the flexibility to create or modify indexes after the table is created. Local indexes can only be created at the time of table creation and cannot be modified later. Global indexes can be created or modified at any time.

By considering these factors, you can make an informed decision on whether to choose local indexes or global indexes in DynamoDB based on the specific requirements and characteristics of your application.


# What are the advantages of using a global index in DynamoDB for querying based on attributes other than the primary key?
Using a global index in DynamoDB for querying based on attributes other than the primary key offers several advantages:

Flexibility in Querying: A global index allows you to query the table based on attributes other than the primary key. This provides flexibility in accessing and retrieving items that match specific attribute values, even if they are not part of the primary key. You can perform efficient queries on different attributes, enabling a wider range of query patterns.

Improved Performance: With a global index, you can achieve faster query performance for specific attribute-based queries. The index provides an optimized data structure that allows for efficient retrieval of items based on the indexed attributes. This can result in reduced latency and improved response times for queries.

Reduced Data Scanning: By using a global index, you can avoid the need for full table scans when querying based on non-primary key attributes. Instead of scanning the entire table, the index allows you to directly access the relevant items based on the indexed attributes, resulting in more targeted and efficient queries.

Simplified Data Access: A global index simplifies the process of accessing and retrieving items based on non-primary key attributes. It eliminates the need for complex filtering or scanning operations to find specific items in the table. This can make your application code simpler and more straightforward.

Multi-Region Replication: Global indexes can be created in different AWS Regions, enabling multi-region replication of data. This provides improved availability and durability for your application. You can query the global index in the desired region, reducing the latency for accessing data from different geographic locations.

Independent Provisioned Throughput: Global indexes have their own provisioned throughput, allowing you to allocate separate read and write capacity units for the index. This means you can optimize the throughput specifically for the queries performed on the global index, without impacting the provisioned throughput of the base table.

Overall, using a global index in DynamoDB for querying based on attributes other than the primary key offers increased flexibility, improved performance, simplified data access, and the ability to replicate data across multiple regions. It enhances the querying capabilities of your application and allows for efficient retrieval of items based on non-primary key attributes.

