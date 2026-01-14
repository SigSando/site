---
layout: post
title: "Firewalls" 
nav_enabled: true
nav_order: 3
parent: Networking notes
---

{: .text-center }
# Firewalls

![firel](/site/assets/firel.png){: width="auto" height="auto" }

{: .text-center }
## <span style="color: orange; font-weight: bold;">What are firewalls & what do they do?</span>

###### In progress ***December 30, 2025*** - Last updated 12/2025

## Firewalls

Firewalls are often implemented by companies and individuals to enchance security. They are the first thing that passes or rejects traffic - since they are traditionally set up at the <u>edge</u>.

(Being at the edge of the network means that a home user would set this up inbetween their <u>Modem</u> and the <u>router</u>.)



- a Firewall allows or denies traffic based on the rules that are set up. Common fields will include; Name, Description, Interface, Allow/Deny, Source IP/group, Destination IP/Group, Ports, and block all, whitelists, blacklists.


- Many types of firewalls are implemented. Here is a short list of some examples:
- a WAF (web application firewall), protects web-based applications
- a Cloud Firewall, protects data transfer in cloud enviroments
- multiple firewalls can be used in conjunction to more efficently route data, as well as having a layered network management. 

- what do Firewall rules look like? 
-Typically, firewall rules are very complicated. They require prior knowledge of the existing firewall rules. 


PowerShell Ex:
> FirewallRule1 -DisplayName "Allow HTTPS" - Direction Inbound  -Protocol -TCP -LocalPort 80 -Action Allow
> FirewallRule2 -DisplayName "Block All others" - Direction Any
-Protocol -Any -LocalPort Any -Action Block


### Why is seperating devices so important? 

- Not all devices should have the ability to reach a `Domain Controller` or a `Medical Device` or a `Manufacturing Sensor`.

- Often it does not make sense to allow devices to talk back and forth with every other device around it, often is it the case that it will technically create a larger and larger network until it is too big to manage. in other words it creates a larger attack surface or widens the network too much.

- Not all access points can reach the same infrastructure as other APs, so it is impossible to have a large area or WAN on the same network. Although most of the time they share the same necessary infrastructure to provide internet access. 

- When we look at at the reason for a subnet, partially it is to divide a network into smaller, more efficient networks.

- Another reason could be to seperate physical areas and regions such as a engineering department, sales group, 1st, 2nd, 3rd floor, and so on.

## Guest Network
- a Guest Network will be a seperate network that is only for visitors. for every reason

## VLAN
- a `VLAN` stands for Virtual Local Area Network. This is a logical segmentation configured on a network switch. This is commonly used for seperating different areas of business such as IT and HR for a company or different departments like a surgical ward and medical offices in a hospital


## DMZ

- a `DMZ` or de-militarized zone, is a subnet or `sub-network` that seperates a `LAN` Local area network, from untrusted networks or devices. 

- Usually a DMZ will face outwards, protecting the business enviroment and internal LANs. 

- Firewalls are a major part of network security, any application or user will have to be compliant to the firewall in order to reach outbound to the World Wide Web/Internet.

- Standard abilities of a firewall will monitor and control network traffic.

- Packet filtering for individual packets, stateful inspection of packets(Comparing previously passed packets), 

- NGFW(Next Gen Firewalls) Provide 
