---
title: What is and how Routing Table works in Microsoft Azure
date: 2023-03-13T15:08:52-03:00
draft: false
description: Network traffic management is a critical challenge for any business, especially those running their services in the cloud. This is where Microsoft Azure's Routing Table comes into play, allowing you to control the flow of network traffic within and outside your virtual network.
author: Marcos Ferreira
---

Network traffic management is a critical challenge for any business, especially those running their services in the cloud. This is where Microsoft Azure's Routing Table comes into play, allowing you to control the flow of network traffic within and outside your virtual network.

<!-- ![Virtual network example](/static/images/azure-posts/routing-table.png "VNET/SUBNET configuration") -->

## What is a Routing Table?
A routing table is a table used by a router or other network device to decide where to forward network packets. In Microsoft Azure, a routing table is used to control network traffic within a virtual network.

The routing table contains a table of routes, each with a network prefix and a next hop. The network prefix is the destination network IP address, while the next hop is the IP address of the next device in the network to which the traffic should be forwarded.

## How Does It Work?
When network traffic enters a Microsoft Azure virtual network, the routing table is used to decide where to forward it. The routing table is associated with a specific virtual subnet and contains several routes that specify how traffic should be routed. Each route has a network prefix that indicates the range of IP addresses that the route applies to.

The routing table examines the destination IP address of the network packet and then looks for a corresponding route that can forward the packet. If there are multiple routes that match the destination IP address prefix, the route with the lowest metric is chosen. The metric is a measure of how preferable a route is compared to other routes. The lower the metric, the more preferable the route.

## Conclusion
The routing table is an important resource for controlling network traffic in Microsoft Azure. With it, you can direct traffic where you want, creating more secure and efficient virtual networks. This also helps reduce latency, optimize performance, and improve network availability. We hope this article has helped you better understand how the routing table works in Azure and how it can be useful in your cloud projects.