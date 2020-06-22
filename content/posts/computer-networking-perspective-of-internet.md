---
title: "Computer Networking Perspective of the Internet"
date: 2020-05-22T09:32:14+08:00
categories: []
tags: []
draft: true
---

1. Nuts and Bolts vs. 2. Infrastructure

1. Nuts and Bolts (Hardware and software that makes up the Internet)

End systems are connected together by a network of communication links and packet switches.
comm links: 
coaxial cable, copper wire, optical fiber, and radio spectrum.

packet switches:
routers and link-layer switches.
 Link-layer switches are typically used in access networks, while routers are typically used in the network core.

 End systems, packet switches, and other pieces of the Internet run protocols that control the sending and receiving of information within the Internet. The Transmission Control Protocol (TCP) and the Internet Protocol (IP) are two of the most important protocols in the Internet. The IP protocol specifies the format of the packets that are sent and received among routers and end systems.


 2. Services description, describe the Internet from an entirely different angle—namely, as an infrastructure that provides
services to applications. 

what kinda applications: The applications are said to be distributed applications, since they involve multiple end systems that exchange data with each other. Importantly, Internet applications run on end systems— they do not run in the packet switches in the network core. Although packet switches facilitate the exchange of data among end systems, they are not concerned with the application that is the source or sink of data.

End systems attached to the Internet provide a socket interface that specifies how a program running on one end system asks the Internet infrastructure to deliver data to a specific destination program running on another end system. This Internet socket interface is a set of rules that the sending program must follow so that the Internet can deliver the data to the destination program.


what is a protocol

A protocol defines the format and the order of messages exchanged between two or more communicating entities, as well as the actions taken on the transmission and/or receipt of a message or other event.

