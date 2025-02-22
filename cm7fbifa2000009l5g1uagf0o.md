---
title: "VPC: What I've Learned and How It Works"
datePublished: Fri Feb 21 2025 22:03:34 GMT+0000 (Coordinated Universal Time)
cuid: cm7fbifa2000009l5g1uagf0o
slug: vpc-what-ive-learned-and-how-it-works
tags: blog, virtual-machine, cloud-computing, hashnode, vpc

---

###   

*<mark>Creating Virtual Machines in the Cloud</mark>*  
To create virtual machines in the cloud, specific resources are required. These resources are like configuring the amount of RAM and the required hard disk space for the server before installing the operating system or running applications. Virtual Private Cloud is used for networking purposes. In the cloud, we need to configure the network first before we host or run any service.  
*<mark>Virtual Private Cloud</mark>*  
Similar to a house with a compound wall, we can consider the compound wall as the VPC, which is a Virtual Private Cloud. When we want to launch a server on the cloud, we create a network called VPC. Once the network is created, companies don’t use the same network for all their services as they need to isolate them. Just as a house is divided into rooms according to our needs, like a kitchen for cooking and a bedroom for sleeping, the network is similarly split into something called subnets. Like in a house, the kitchen, bedrooms, or the living room can be considered different subnets within the network.  
*<mark>Public and Private Subnets</mark>*  
Private and public subnets are two types of subnets. Services hosted on public subnets can be accessed by the public. Comparing this to the example above, since relatives and friends will have access only to the living room, the living room can be considered a public subnet, while the bedroom and kitchen can be considered private subnets.  
*<mark>Internet Gateway and Route Tables</mark>*  
Anyone who wants access to this VPC network would need an internet gateway. In the example above, it can be compared to the front gate of the house. All the other doors inside the house after passing through the internet gateway are called route tables. These route tables contain rules that determine which path to take when a user tries to access something on the network. By default, a route table is created when we first configure the VPC.  
*<mark>Accessing Private Subnets</mark>*  
Now, if we want to enter the living room, we have access through the front gate, then the main entrance. However, from the front gate, which is the internet gateway, we don’t have direct access to the inside bedrooms or kitchen, which in technical terms means no direct access to private subnets. To access private subnet services, the only way is using the internet gateway. This allows us to access the public subnets first, and only through the public subnets can we connect to the private subnets. Basically, database servers and application servers are always located on private subnets to guarantee that no other parties or unauthorized users may access them. The web server is placed on a public subnet for the general public.  
*<mark>NAT Gateway for Private Subnets</mark>*  
Private subnets will have no internet connection, but public subnets have internet access. Database and application servers are hosted in private subnets, so that no one can access them directly from the internet gateway, but we can access them by connecting to the web server hosted on the public subnet. A question can come to our mind: if the private subnet doesn’t have internet access, how can we deploy applications on these servers or download code files onto these private subnet servers? This is where NAT Gateway comes into the picture.

We always create a NAT Gateway in the public subnet. All the route tables of private subnets are connected to the NAT Gateway in the public subnet. NAT stands for Network Address Translation. It only handles outgoing traffic from private subnets but does not allow incoming traffic. So, whenever you want to download something from these private servers, you can use the NAT Gateway, but any other third party cannot access it.  
*<mark>Security with NACLs and Security Groups</mark>*  
We use Network Access Control Lists and Security Groups for security. NACLs control access at the subnet level, specifying who is allowed to connect to each subnet. Security Groups operate at the resource or server level. While Security Groups permit access, NACLs can be configured to both permit and deny traffic. Security Groups also regulate which ports can be accessed for the servers hosted in public subnets. When a subnet is created, a NACL with default rules is automatically assigned, whereas Security Groups need to be configured separately.  
*<mark>VPC Flow Logs</mark>*  
We also have something called VPC Flow Logs, which provide details on who accessed the server, from which server they moved, at what time, and other such information. It’s similar to how a watchman maintains a record of who entered the building, when they left, and which vehicle came in.