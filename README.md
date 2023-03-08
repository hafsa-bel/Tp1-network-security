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

- *PC8* (**200.4.1.2**) and *PC9* (**200.4.1.3**) are in the same network **200.4.1.0**
- *PC10* (**200.4.2.2**) and *PC11* (**200.4.2.3**) are in the same network **200.4.2.0**
- *PC0* (**200.4.3.2**) and *PC14* (**200.4.3.3**) are in the same network **200.4.3.0**
- *PC12* (**200.4.4.2**) and *PC13* (**200.4.4.3**) are in the same network **200.4.4.0**

Then we're going to configure routers.

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222971632-07f37395-010f-4fe4-afbf-1ff8029bcb7e.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222971633-59da793b-cebe-46dc-8bc8-24f043d96aef.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/222971634-1f0c0522-8c22-49d9-b743-aa7ee79bc21c.png">
</p>

The images show static routing applied to our routers.

# ACL:

 <ins>*What is an ACL?*</ins>
   
- Access Control Lists “ACLs” are network traffic filters that can control incoming or outgoing traffic.

- ACLs work on a set of rules that define how to forward or block a packet at the router’s interface.

- An ACL is the same as a Stateless Firewall, which only restricts, blocks, or allows the packets that are flowing from source to destination.

- When you define an ACL on a routing device for a specific interface, all the traffic flowing through will be compared with the ACL statement which will either block it or allow it.

- The criteria for defining the ACL rules could be the source, the destination, a specific protocol, or more information.

- ACLs are common in routers or firewalls, but they can also configure them in any device that runs in the network, from hosts, network devices, servers, etc.

<ins>*Why using an ACL?*</ins>
 
The main idea of using an ACL is to provide security to your network. Without it, any traffic is either allowed to enter or exit, making it more vulnerable to unwanted and dangerous traffic.

To improve security with an ACL you can, for example, deny specific routing updates or provide traffic flow control.

As shown in the picture below, the routing device has an ACL that is denying access to host C into the Financial network, and at the same time, it is allowing access to host D.

<p align="center">
  <img src="https://user-images.githubusercontent.com/73228919/222972088-4045f7e0-d9d7-48d5-bca0-7b045d1aabe1.jpeg">
</p>

With an ACL you can filter packets for a single or group of IP address or different protocols, such as TCP or UDP.

So for example, instead of blocking only one host in the engineering team, you can deny access to the entire network and only allow one. Or you can also restrict the access to host C.

If the Engineer from host C, needs to access a web server located in the Financial network, you can only allow port 80, and block everything else.

<ins>*Where to place an ACL ?*</ins>

The devices that are facing unknown external networks, such as the Internet, need to have a way to filter traffic. So, one of the best places to configure an ACL is on the edge routers.

A routing device with an ACL can be placed facing the Internet and connecting the DMZ (De-Militarized Zone), which is a buffer zone that divides the public Internet and the private network.

The DMZ is reserved for servers that need access from the outside, such as Web Servers, app servers, DNS servers, VPNs, etc.

As shown in the picture below, the design shows a DMZ divided by two devices, one that separates the trusted zone from the DMZ and another that separates it with the Internet (public network).

<p align="center">
  <img src="https://user-images.githubusercontent.com/73228919/222972241-2c19f32f-b1eb-4973-8fa6-9dfb3349fd61.jpeg">
</p>

<ins>*How to implement ACLs in our routers?*</ins>

We have **4** questions in this practical course :
1) Allow packets sent from the machine 200.4.1.2 and deny packets from the machine 200.4.1.3.
2) Deny packets coming from the machine 200.4.3.3 and going to the networks 200.4.2.0 and 200.4.1.0.
3) Deny packets originating from the network 200.4.4.0 and going to the network 200.4.3.0.
3) Deny pings (ICMP) coming from the network 200.4.2.0 and going to 200.4.1.0, and only allow pings from the machine 200.4.2.3.

### Answers:

***Question 1 :***

In this question we're going to use standard ACL.

<p align="center">
  <img src="https://user-images.githubusercontent.com/73228919/223749334-b3dd54ce-9d69-45ed-ad2d-29850811ff54.png">
</p>

&emsp; Here's the ip address of this machine: &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; We're going to check with pinging: 

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/223752443-744fa24a-1b9a-4f27-908b-977def2a5930.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/223752420-e0f4a169-2332-4cdc-8499-3fd246c83145.png">
</p>

As we can see we cannot send packets from **200.4.1.3** to **200.4.3.0**

&emsp; Here's the ip address of this machine: &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; We're going to check with pinging: 

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/223756354-34740439-a16a-4f34-ac41-1459903b2be3.png">
  <img width="500" src="https://user-images.githubusercontent.com/73228919/223756379-a1e256c6-8d6c-4bd6-834e-8edae5724c84.png">
</p>

As we can see we can send packets from **200.4.1.2** to **200.4.3.0**

***Question 2 :***

In this question we're going to use extended ACL to filter packets based on the destination address. Standard ACLs do not allow specifying a range of addresses for the destination; they only allow filtering on a specific IP address or subnet.

Therefore, the extended ACL is used to filter packets based on criteria such as source IP address, destination IP address, protocol, port number, etc. In this specific case, we need to filter packets that have a destination address in two different networks, which requires the use of an extended ACL.

<p align="center">
  <img src="https://user-images.githubusercontent.com/73228919/223758258-2154889b-0981-42fc-89f5-fc8b3ef010f5.png">
</p>









