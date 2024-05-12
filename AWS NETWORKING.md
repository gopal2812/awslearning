# Introduction to Amazon VPC
A VPC is an isolated network you create in the AWS cloud, similar to a traditional network in a data center. When you create a VPC, you need to choose three main things. 

The name of your VPC.

A Region for your VPC to live in. Each VPC spans multiple Availability Zones within the Region you choose.

A IP range for your VPC in CIDR notation. This determines the size of your network. Each VPC can have up to four /16 IP ranges.

 Using this information, AWS will provision a network and IP addresses for that network.    


Create a Subnet After you create your VPC, you need to create subnets inside of this network. Think of subnets as smaller networks inside your base network—or virtual area networks (VLANs) in a traditional, on-premises network. In an on-premises network, the typical use case for subnets is to isolate or optimize network traffic. In AWS, subnets are used for high availability and providing different connectivity options for your resources. When you create a subnet, you need to choose three settings.

The VPC you want your subnet to live in, in this case VPC (10.0.0.0/16).

The Availability Zone you want your subnet to live in, in this case AZ1.

A CIDR block for your subnet, which must be a subset of the VPC CIDR block, in this case 10.0.0.0/24.

 When you launch an EC2 instance, you launch it inside a subnet, which will be located inside the Availability Zone you choose.     


High Availability with A VPC When you create your subnets, keep high availability in mind. In order to maintain redundancy and fault tolerance, create at least two subnets configured in two different Availability Zones.   

As you learned earlier in the trail, it’s important to consider that “everything fails all the time.” In this case, if one of these AZs fail, you still have your resources in another AZ available as backup.   


Reserved IPs For AWS to configure your VPC appropriately, AWS reserves five IP addresses in each subnet. These IP addresses are used for routing, Domain Name System (DNS), and network management.  

For example, consider a VPC with the IP range 10.0.0.0/22. The VPC includes 1,024 total IP addresses. This is divided into four equal-sized subnets, each with a /24 IP range with 256 IP addresses. Out of each of those IP ranges, there are only 251 IP addresses that can be used because AWS reserves five.  


Since AWS reserves these five IP addresses, it can impact how you design your network. A common starting place for those who are new to the cloud is to create a VPC with a IP range of /16 and create subnets with a IP range of /24. This provides a large amount of IP addresses to work with at both the VPC and subnet level. 

# Gateways
Internet Gateway 

To enable internet connectivity for your VPC, you need to create an internet gateway. Think of this gateway as similar to a modem. Just as a modem connects your computer to the internet, the internet gateway connects your VPC to the internet. Unlike your modem at home, which sometimes goes down or offline, an internet gateway is highly available and scalable. After you create an internet gateway, you then need to attach it to your VPC.  

Virtual Private Gateway  

A virtual private gateway allows you to connect your AWS VPC to another private network. Once you create and attach a VGW to a VPC, the gateway acts as anchor on the AWS side of the connection. On the other side of the connection, you’ll need to connect a customer gateway to the other private network. A customer gateway device is a physical device or software application on your side of the connection. Once you have both gateways, you can then establish an encrypted VPN connection between the two sides. 

The content you provided is related to connectivity options between AWS and a remote site, such as a data center. It discusses two main options: AWS VPN and AWS Direct Connect.

# AWS VPN: 
It is a common and popular way to securely connect a remote network, like a data center, to AWS. AWS VPN consists of two services: AWS Site-Site VPN and AWS Client VPN. Site-Site VPN is used to connect a customer-managed data center to a VPC, while Client VPN is used for administrators to connect to AWS or the data center.

# AWS Direct Connect: 
It provides a hosted private connection to AWS through a Direct Connect delivery partner or AWS itself. It offers a private dedicated connection that bypasses the public internet, reducing latency and increasing reliability. It is suitable for high-volume traffic and requires reliability in throughput.

Here are some benefits of using AWS Direct Connect over a VPN connection:

Enhanced Performance: AWS Direct Connect provides a private dedicated connection that bypasses the public internet. This means that while the data is in transit, it remains on the AWS global network and never touches the public internet. As a result, it reduces the chance of hitting bottlenecks or unexpected increases in latency, providing a more reliable and consistent performance compared to a VPN connection.

Higher Throughput: AWS Direct Connect supports larger and more reliable throughput, making it suitable for sending a high volume of traffic to AWS. If you have applications or workloads that require a significant amount of data transfer, Direct Connect can provide the necessary reliability and throughput.

Improved Security: With AWS Direct Connect, you establish a private connection between your on-premises data center and AWS. This private connection is not exposed to the public internet, reducing the risk of potential security threats. It provides an additional layer of security for your data and resources.

Hybrid Deployments: AWS Direct Connect is particularly useful for hybrid deployments, where you have some resources hosted in AWS and others in an on-premises data center. It allows you to seamlessly connect your on-premises network to your VPC in AWS, enabling a hybrid architecture that combines the benefits of both environments.

It's important to note that the choice between AWS Direct Connect and a VPN connection depends on your specific use case and requirements. In some cases, a VPN connection may be sufficient, while in others, AWS Direct Connect may be the preferred option. It's always recommended to evaluate your needs and consider factors like performance, throughput, and security when making a decision.

AWS Direct Connect can be more beneficial for hybrid deployments in the following scenarios:

Data Transfer Intensive Workloads: If you have data transfer-intensive workloads that require large volumes of data to be transferred between your on-premises data center and AWS, AWS Direct Connect can provide higher throughput and more reliable performance compared to AWS VPN. This can be particularly advantageous for scenarios such as data backups, data replication, or large-scale data migrations.

Low Latency Requirements: If your applications or workloads have strict low latency requirements, AWS Direct Connect can offer a more consistent and predictable network performance compared to AWS VPN. This is because the data sent over Direct Connect remains on the AWS global network and avoids the potential bottlenecks or latency fluctuations that can occur over the public internet.

Enhanced Security Needs: If you have stringent security requirements or deal with sensitive data, AWS Direct Connect can provide an additional layer of security. By establishing a private connection between your on-premises network and AWS, Direct Connect ensures that your data does not traverse the public internet, reducing the risk of potential security threats.

Large-scale Workloads: If you have large-scale workloads that require high availability, reliability, and consistent performance, AWS Direct Connect can be beneficial. It offers a dedicated connection that is not shared with other users, providing a more stable and reliable network connection for your critical workloads.

Compliance and Regulatory Requirements: If your organization operates in an industry with strict compliance or regulatory requirements, AWS Direct Connect can help meet those requirements by providing a private and dedicated connection that ensures data privacy and security.

It's important to assess your specific needs and requirements when considering AWS Direct Connect for hybrid deployments. Evaluating factors such as data transfer volume, latency requirements, security needs, workload scale, and compliance requirements will help determine if AWS Direct Connect is the more beneficial option for your hybrid architecture.

ere's an example scenario where using AWS Direct Connect can be more cost-effective than AWS VPN:

Let's say you have a large enterprise with multiple branch offices spread across different locations. Each branch office needs to connect to your AWS resources in a Virtual Private Cloud (VPC) for various operations. In this case, you have two options for connectivity: AWS Direct Connect and AWS VPN.

AWS VPN: If you choose to use AWS VPN, each branch office would establish a VPN connection over the public internet to connect to the VPC. While AWS VPN is a cost-effective option, the cost can increase as the number of branch offices and the volume of data transfer grows. The cost is typically based on factors such as the number of VPN connections, data transfer rates, and the amount of data transferred.

AWS Direct Connect: On the other hand, if you opt for AWS Direct Connect, you can establish a dedicated private connection between your on-premises network and AWS. This connection can be shared across multiple branch offices, reducing the number of individual VPN connections required. With AWS Direct Connect, you pay for the dedicated connection and any associated data transfer, which can be more cost-effective compared to multiple VPN connections.

In this scenario, using AWS Direct Connect can be more cost-effective because:

Reduced VPN Connection Costs: By using a single AWS Direct Connect connection shared across multiple branch offices, you can reduce the number of individual VPN connections required. This can result in cost savings compared to setting up and maintaining multiple VPN connections.

Data Transfer Savings: AWS Direct Connect can offer cost savings for data transfer, especially if you have a high volume of data transfer between your branch offices and the AWS VPC. With AWS Direct Connect, you can potentially benefit from reduced data transfer costs compared to transferring data over VPN connections.

It's important to note that the cost-effectiveness of AWS Direct Connect versus AWS VPN depends on various factors, including the number of branch offices, data transfer volume, and specific pricing details. It's recommended to evaluate your specific requirements and consult the AWS pricing documentation to determine the most cost-effective option for your organization.

# ACLs and security groups
In AWS, network ACLs and security groups have different default configurations. Here's how they differ:

## Network ACLs:
By default, network ACLs allow all inbound and outbound traffic.
You can modify the configurations of network ACLs to further lock down your subnets by adding specific rules to allow or deny traffic.

## Security Groups:
By default, security groups block all inbound traffic and allow all outbound traffic.
You need to explicitly open inbound ports in security groups to allow specific types of traffic to reach your EC2 instances.
So, while network ACLs start with an open configuration and require you to add rules to restrict traffic, security groups start with a closed configuration and require you to add rules to allow inbound traffic.


# What is the purpose of network ACLs in securing VPC resources in AWS?
The purpose of network ACLs (Access Control Lists) in securing VPC (Virtual Private Cloud) resources in AWS is to control and filter the traffic that enters and leaves your subnets. Here's how network ACLs contribute to the security of your VPC resources:

Subnet-level Firewall: Network ACLs act as a firewall at the subnet level, allowing you to control what kind of traffic is allowed to enter and leave your subnets.

Traffic Filtering: With network ACLs, you can create rules to allow or deny specific types of traffic based on protocols, ports, and IP addresses. This helps you enforce security policies and restrict unauthorized access to your resources.

Fine-Grained Control: Network ACLs provide granular control over inbound and outbound traffic at the subnet level. You can create rules to allow or deny traffic from specific IP addresses or ranges, giving you the flexibility to define precise access rules.

Stateless Filtering: Network ACLs are considered stateless, which means that you need to include both inbound and outbound ports used for the protocols you want to allow. This ensures that the traffic is allowed in and the corresponding response can leave the subnet.

By using network ACLs effectively, you can enhance the security of your VPC resources by controlling the flow of traffic and preventing unauthorized access.

# What is the default configuration of network ACLs in AWS?
The default configuration of network ACLs in AWS allows all inbound and outbound traffic. When you create a new VPC (Virtual Private Cloud), it is isolated from internet traffic by default, which provides a basic level of security. However, when you start allowing internet traffic by opening up routes, you may need to modify the configurations of your network ACLs to further secure your subnets.

It's important to note that while the default network ACL configuration allows all traffic, you have the flexibility to customize and modify the rules to meet your specific security requirements. You can add rules to allow or deny specific types of traffic based on protocols, ports, and IP addresses, providing you with fine-grained control over the traffic flow in your VPC.

# What are the main differences between network ACLs and security groups in AWS?
Network ACLs and security groups in AWS are both used for securing resources within a VPC (Virtual Private Cloud), but they have some key differences:

Network ACLs:

Operate at the subnet level: Network ACLs act as a firewall at the subnet level, controlling inbound and outbound traffic for all resources within the subnet.
Stateless: Network ACLs are stateless, meaning that you need to define both inbound and outbound rules separately to allow traffic in both directions.
Allow and deny rules: Network ACLs support both allow and deny rules, giving you more control over traffic filtering.
Applied to subnets: Network ACLs are associated with subnets and are applied to all resources within that subnet by default.
Security Groups:

Operate at the instance level: Security groups act as a firewall at the individual EC2 instance level, controlling inbound and outbound traffic for each instance.
Stateful: Security groups are stateful, meaning that if you allow inbound traffic, the corresponding outbound traffic is automatically allowed, simplifying rule configuration.
Allow rules only: Security groups only support allow rules, meaning that you can specify which protocols, ports, and IP addresses are allowed, but you cannot explicitly deny traffic.
Applied to instances: Security groups are associated with individual EC2 instances and are applied to the instance itself, rather than the subnet.

# How can you modify the default configuration of network ACLs in AWS?
To modify the default configuration of network ACLs in AWS, you can make changes to the rules associated with the ACL. Here's how you can do it:

Open the Amazon VPC console.
In the navigation pane, choose "Network ACLs".
Select the network ACL that you want to modify.
In the "Inbound Rules" or "Outbound Rules" tab, you will see the default rules that are currently in place.
To modify a rule, select it and choose "Edit".
You can then change the rule's properties, such as the rule number, protocol, port range, and the action (allow or deny).
After making the desired changes, choose "Save" to apply the modifications.
By modifying the rules of the network ACL, you can further lock down your subnets and control the traffic that is allowed to enter and leave. It's important to carefully consider the changes you make to ensure that your network ACL configuration aligns with your security requirements.

# How do network ACLs and security groups complement each other in securing VPC resources?
Network ACLs and security groups in AWS complement each other in securing VPC (Virtual Private Cloud) resources by providing different layers of security at different levels. Here's how they work together:

Network ACLs: Network ACLs act as a firewall at the subnet level, controlling inbound and outbound traffic for all resources within the subnet. They provide the following benefits:

Traffic Filtering: Network ACLs allow you to define rules to allow or deny specific types of traffic based on protocols, ports, and IP addresses.
Subnet-level Control: Network ACLs apply to all resources within a subnet, providing a broader level of control over traffic flow.
Stateless Filtering: Network ACLs require separate rules for inbound and outbound traffic, ensuring that both directions are properly configured.
Security Groups: Security groups act as a firewall at the individual EC2 instance level, controlling inbound and outbound traffic for each instance. They offer the following advantages:

Instance-level Control: Security groups are associated with individual EC2 instances, allowing you to define specific rules for each instance.
Stateful Filtering: Security groups are stateful, meaning that if you allow inbound traffic, the corresponding outbound traffic is automatically allowed, simplifying rule configuration.
Allow Rules Only: Security groups support allow rules, specifying which protocols, ports, and IP addresses are allowed, but they do not support explicit deny rules.
By using both network ACLs and security groups together, you can create a layered approach to security within your VPC:

Network ACLs provide a first line of defense at the subnet level, allowing you to filter traffic before it reaches the instances.
Security groups provide a second layer of defense at the instance level, allowing you to control traffic specific to each instance.
This combination of network ACLs and security groups allows you to implement a comprehensive security strategy, providing granular control over traffic flow and enhancing the overall security of your VPC resources.

# How can you determine if a subnet in AWS has public access?
To determine if a subnet in AWS has public access, you need to check the associated route table. Here's how you can do it:

Go to the AWS Management Console and navigate to the VPC service.
Click on "Subnets" in the left-hand menu.
Find the subnet you want to check and note its ID.
Click on the subnet ID to view its details.
In the "Details" tab, look for the "Route table" field and note the associated route table ID.
Go back to the VPC service and click on "Route Tables" in the left-hand menu.
Find the route table ID you noted earlier and click on it to view its details.
Look for a route in the route table with a destination of "0.0.0.0/0" (which represents all internet traffic).
If such a route exists and its target is an internet gateway, then the subnet has public access. If there is no route to an internet gateway, then the subnet does not have public access.
By following these steps, you can determine whether a subnet in AWS has public access based on its associated route table.

# Can you explain the difference between the main route table and custom route tables in AWS?
Certainly! In AWS, there are two types of route tables: the main route table and custom route tables. Here's the difference between them:

# Main Route Table:

When you create a new Virtual Private Cloud (VPC) in AWS, a main route table is automatically created and associated with the VPC.
The main route table controls the routing for the entire VPC.
By default, the main route table allows traffic between all subnets within the VPC.
It has a default local route that enables communication between all resources within the VPC.
You cannot delete the main route table, but you can modify its routes and associations.

# Custom Route Tables:
Custom route tables are additional route tables that you can create and associate with your subnets within a VPC.
They allow you to have more granular control over the routing of network traffic within your VPC.
You can create custom route tables to define specific routes for subnets based on your requirements.
Each custom route table can have its own set of routes and associations.
You can associate multiple subnets with a custom route table, allowing you to control the traffic flow between those subnets.
Custom route tables are useful when you want to create different routing configurations for different subnets within your VPC.
In summary, the main route table is automatically created when you create a VPC and controls the routing for the entire VPC. Custom route tables, on the other hand, are additional route tables that you can create and associate with specific subnets to have more control over the routing of network traffic within your VPC.

# How does the local route in a route table enable communication within a VPC?
The local route in a route table plays a crucial role in enabling communication within a Virtual Private Cloud (VPC) in AWS. Here's how the local route facilitates communication within a VPC:

Default Configuration: When you create a new VPC in AWS, a main route table is automatically created and associated with the VPC. The main route table has a default local route.

Local Route Definition: The local route in the route table has a destination that represents the IP address range or CIDR block of the VPC itself. It typically looks like "local" or "VPC CIDR/16" (e.g., 10.0.0.0/16).

Traffic Flow: The local route allows traffic to flow freely within the VPC. It enables communication between all resources (such as instances, subnets, and other services) that are part of the VPC.

Resource Accessibility: With the local route, resources within the VPC can communicate with each other using their private IP addresses. For example, an instance in one subnet can communicate with an instance in another subnet within the same VPC without going through an internet gateway.

Isolation: The local route also ensures that communication is isolated within the VPC. It does not allow traffic to flow outside the VPC unless additional routes are defined in the route table.

In summary, the local route in a route table allows for communication within a VPC by enabling traffic flow between resources within the VPC using their private IP addresses. It ensures that resources within the VPC can communicate with each other while maintaining isolation from external networks unless additional routes are configured.

# Can you explain the difference between public and private access for a subnet based on its associated route table?
The difference between public and private access for a subnet in AWS is determined by the routes defined in its associated route table. Here's an explanation of public and private access based on the associated route table:

Public Access:

A subnet is considered to have public access if its associated route table has a route to an internet gateway.
An internet gateway is a horizontally scalable, redundant, and highly available AWS service that allows communication between instances in a VPC and the internet.
When a subnet has a route to the internet gateway, instances within that subnet can send and receive traffic to and from the internet.
This enables resources in the subnet to have public IP addresses and be directly accessible from the internet.
Private Access:

A subnet is considered to have private access if its associated route table does not have a route to an internet gateway.
In this case, instances within the subnet cannot directly send or receive traffic from the internet.
Resources in the subnet typically have private IP addresses and are not directly accessible from the internet.
Private subnets are commonly used for resources that do not require direct internet connectivity, such as backend servers or databases.
It's important to note that the public or private access designation is based on the routes defined in the associated route table, not the subnet itself. By configuring the routes in the route table, you can control whether a subnet has public or private access, allowing you to tailor the network connectivity of your resources based on your requirements.

Remember that public and private access are not absolute terms, but rather relative to the associated route table's configuration. A subnet can have public access in one route table and private access in another, depending on the routes defined in each route table.

# What happens if a subnet is not associated with any custom route table in AWS?
If a subnet in AWS is not associated with any custom route table, it will automatically use the main route table of the VPC. Here's what happens when a subnet is not associated with a custom route table:

Default Association: When you create a subnet within a VPC, it is automatically associated with the main route table of that VPC. The main route table is created by default when the VPC is created.

Default Routing: The main route table has a default configuration that allows traffic to flow between all subnets within the VPC. This means that instances within the subnet can communicate with other instances in the same VPC, regardless of the subnet they are in.

Local Route: The main route table contains a local route that enables communication within the VPC. This local route allows traffic to flow between resources within the VPC using their private IP addresses.

No Custom Routes: Since the subnet is not associated with a custom route table, it does not have any additional routes defined specifically for that subnet. It relies solely on the routes defined in the main route table.

Limited Control: Without a custom route table, you have limited control over the routing of traffic for that specific subnet. You cannot define custom routes or control the flow of traffic to or from the internet.

In summary, if a subnet is not associated with any custom route table, it will use the main route table of the VPC. This allows for communication within the VPC using the local route defined in the main route table. However, you have limited control over the routing of traffic for that subnet and cannot define custom routes or control internet access specifically for that subnet.

# Can you explain how the local route in the main route table enables communication within a VPC?
The local route in the main route table of a Virtual Private Cloud (VPC) in AWS enables communication within the VPC. Here's how the local route facilitates communication within a VPC:

Default Configuration: When you create a new VPC in AWS, a main route table is automatically created and associated with the VPC. The main route table is the default route table for the VPC.

Local Route Definition: The main route table contains a local route that has a destination representing the IP address range or CIDR block of the VPC itself. This local route typically looks like "local" or "VPC CIDR/16" (e.g., 10.0.0.0/16).

Traffic Flow: The local route in the main route table allows traffic to flow freely within the VPC. It enables communication between all resources (such as instances, subnets, and other services) that are part of the VPC.

Resource Accessibility: With the local route, resources within the VPC can communicate with each other using their private IP addresses. For example, an instance in one subnet can communicate with an instance in another subnet within the same VPC without going through an internet gateway.

Isolation: The local route ensures that communication is isolated within the VPC. It does not allow traffic to flow outside the VPC unless additional routes are defined in the main route table.

In summary, the local route in the main route table of a VPC allows for communication within the VPC by enabling traffic flow between resources within the VPC using their private IP addresses. It ensures that resources within the VPC can communicate with each other while maintaining isolation from external networks unless additional routes are configured.

## Amazon VPC Routing and Security
# The Main Route Table
When you create a VPC, AWS creates a route table called the main route table. A route table contains a set of rules, called routes, that are used to determine where network traffic is directed. AWS assumes that when you create a new VPC with subnets, you want traffic to flow between them. Therefore, the default configuration of the main route table is to allow traffic between all subnets in the local network. Below is an example of a main route table:   


There are two main parts to this route table.

The destination, which is a range of IP addresses where you want your traffic to go. In the example of sending a letter, you need a destination to route the letter to the appropriate place. The same is true for routing traffic. In this case, the destination is the IP range of our VPC network.

The target, which is the connection through which to send the traffic. In this case, the traffic is routed through the local VPC network.

# Custom Route Tables
While the main route table controls the routing for your VPC, you may want to be more granular about how you route your traffic for specific subnets. For example, your application may consist of a frontend and a database. You can create separate subnets for these resources and provide different routes for each of them.

If you associate a custom route table with a subnet, the subnet will use it instead of the main route table. By default, each custom route table you create will have the local route already inside it, allowing communication to flow between all resources and subnets inside the VPC. 


# Secure Your Subnets with Network ACLs
Think of a network ACL as a firewall at the subnet level. A network ACL enables you to control what kind of traffic is allowed to enter or leave your subnet. You can configure this by setting up rules that define what you want to filter. Here’s an example.

Inbound






Rule #

Type

Protocol

Port Range

Source

Allow/Deny

100

All IPv4 traffic

All

All

0.0.0.0/0

ALLOW

*

All IPv4 traffic

All

All

0.0.0.0/0

DENY

Outbound






Rule #

Type

Protocol

Port Range

Source

Allow/Deny

100

All IPv4 traffic

All

All

0.0.0.0/0

ALLOW

*

All IPv4 traffic

All

All

0.0.0.0/0

DENY

The default network ACL, shown in the table above, allows all traffic in and out of your subnet. To allow data to flow freely to your subnet, this is a good starting place.   However, you may want to restrict data at the subnet level. For example, if you have a web application, you might restrict your network to allow HTTPS traffic and remote desktop protocol (RDP) traffic to your web servers.

Inbound






Rule #

Source IP

Protocol

Port

Allow/Deny

Comments

100

All IPv4 traffic

TCP

443

ALLOW

Allows inbound HTTPS traffic from anywhere

130

192.0.2.0/24

TCP

3389

ALLOW

Allows inbound RDP traffic to the web servers from your home network’s public IP address range (over the internet gateway)

*

All IPv4 traffic

All

All

DENY

Denies all inbound traffic not already handled by a preceding rule (not modifiable)

Outbound






Rule #

Destination IP

Protocol

Port

Allow/Deny

Comments

120

0.0.0.0/0

TCP

1025-65535

ALLOW

Allows outbound responses to clients on the internet (serving people visiting the web servers in the subnet)

*

0.0.0.0/0

All

All

DENY

Denies all outbound traffic not already handled by a preceding rule (not modifiable)

Notice that in the network ACL example above, you allow inbound 443 and outbound range 1025-65535. That’s because HTTP uses port 443 to initiate a connection and will respond to an ephemeral port. Network ACL’s are considered stateless, so you need to include both the inbound and outbound ports used for the protocol. If you don’t include the outbound range, your server would respond but the traffic would never leave the subnet.   

Since network ACLs are configured by default to allow incoming and outgoing traffic, you don’t need to change their initial settings unless you need additional security layers.

Secure Your EC2 Instances with Security Groups
The next layer of security is for your EC2 Instances. Here, you can create a firewall called a security group. The default configuration of a security group blocks all inbound traffic and allows all outbound traffic.  


You might be wondering: “Wouldn’t this block all EC2 instances from receiving the response of any customer requests?” Well, security groups are stateful, meaning they will remember if a connection is originally initiated by the EC2 instance or from the outside and temporarily allow traffic to respond without having to modify the inbound rules.   

If you want your EC2 instance to accept traffic from the internet, you’ll need to open up inbound ports. If you have a web server, you may need to accept HTTP and HTTPS requests to allow that type of traffic in through your security group. You can create an inbound rule that will allow port 80 (HTTP) and port 443 (HTTPS) as shown below. 

Inbound rules
Type      Protocol PortRange Source

HTTP (80) TCP (6) 80         0.0.0.0/0

HTTP (80) TCP (6) 80         ::/0

HTTPS (443) TCP (6) 443  0.0.0.0/0

HTTPS (443) TCP (6) 443  ::/0

You learned in a previous unit that subnets can be used to segregate traffic between computers in your network. Security groups can be used to do the same thing. A common design pattern is organizing your resources into different groups and creating security groups for each to control network communication between them.   

![image](https://github.com/gopal2812/awslearning/assets/39087216/72a6a924-ed88-4243-9f75-461954e98337)

This example allows you to define three tiers and isolate each tier with the security group rules you define. In this case, you only allow internet traffic to the web tier over HTTPS, Web Tier to Application Tier over HTTP, and Application tier to Database tier over MySQL. This is different from traditional on-premises environments, in which you isolate groups of resources via VLAN configuration. In AWS, security groups allow you to achieve the same isolation without tying it to your network. 
