# Tp1-network-security :

# Introduction : 

  In the computer networking world, an **ACL** is one of the most fundamental components of security.
An Access Control Lists **ACL** is a function that watches incoming and outgoing traffic and compares it with a set of defined statements.
In this practical exercise, we will be working with access lists to configure network security policies. We will learn how to create, modify, and apply access lists to routers and switches, and how to use access lists to filter traffic based on specific requirements.

  But before this let's configure our network schema.

## Schema :

<p align="center">
  <img width="1000" src="https://user-images.githubusercontent.com/73228919/222967517-a8eabcc6-debd-401a-97b9-b37c9183c889.png">
</p>

## Configuration:

First of all we're going to configure the PCs manually.

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968680-4f322300-fdea-4a31-8942-fc18aa7a67d1.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968681-7af1ac84-11e9-400c-b3a0-bd3e877f895c.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968679-679f1fbe-161c-4805-8d0a-1e252e8a4a72.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968684-f1aa977d-5e4a-43c4-b543-7b64e2088965.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968685-47df8152-bc96-4685-a0bf-853080147060.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968688-3c88c2bc-659f-4932-8eb1-21402e85616f.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968690-dcae08c4-14a6-45a9-bd21-bd9940bcd193.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222968691-5312cb94-f4ad-4996-8946-f45b754cbf05.png">
</p>

Then we're going to configure routers.

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222971632-07f37395-010f-4fe4-afbf-1ff8029bcb7e.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222971633-59da793b-cebe-46dc-8bc8-24f043d96aef.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222971634-1f0c0522-8c22-49d9-b743-aa7ee79bc21c.png">
</p>

The images show static routing applied to our routers.

# ACL:

   *What is an ACL?*
   
- Access Control Lists “ACLs” are network traffic filters that can control incoming or outgoing traffic.

- ACLs work on a set of rules that define how to forward or block a packet at the router’s interface.

- An ACL is the same as a Stateless Firewall, which only restricts, blocks, or allows the packets that are flowing from source to destination.

- When you define an ACL on a routing device for a specific interface, all the traffic flowing through will be compared with the ACL statement which will either block it or allow it.

- The criteria for defining the ACL rules could be the source, the destination, a specific protocol, or more information.

- ACLs are common in routers or firewalls, but they can also configure them in any device that runs in the network, from hosts, network devices, servers, etc.

   *Why using an ACL?*
 
The main idea of using an ACL is to provide security to your network. Without it, any traffic is either allowed to enter or exit, making it more vulnerable to unwanted and dangerous traffic.
To improve security with an ACL you can, for example, deny specific routing updates or provide traffic flow control.
As shown in the picture below, the routing device has an ACL that is denying access to host C into the Financial network, and at the same time, it is allowing access to host D.

<p align="center">
  <img src="https://user-images.githubusercontent.com/73228919/222972088-4045f7e0-d9d7-48d5-bca0-7b045d1aabe1.jpeg">
</p>





