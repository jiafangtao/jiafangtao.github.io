---
layout: post
title: "iptable notes"
date: 2025-04-21 08:00:00
authors:
- brucejia
tags: 
  - networking
  - iptables
  - notes
description: "Raw notes of learning iptables"
categories: "notes"
series:
- "Cloud Native"
---

# iptables Notes

The iptables utility allows you to manage the network firewall in Linux distributions. iptables is a popular command-line utility for interacting with the built-in Linux kernel firewall called Netfilter, which has been included in the Linux kernel since version 2.4. 

## How iptables Works
iptables operates using a system of rules. These rules control incoming and outgoing traffic, organized into chains that either allow or block traffic.

A more detailed breakdown of how iptables works is as follows:

Network packets pass through one or more chains.
As a network packet moves through a chain, each rule in that chain is applied to it. During this process, the packet is checked against specified criteria. If it does not meet a criterion, a specific action is applied to it. These actions can include allowing or blocking traffic, among other operations.

## Key iptables Terminology
While working with iptables, you may encounter the following terms:

**Chain**: A sequence or set of rules that determine how traffic will be handled.
**Rules**: Defined actions that contain *criteria* and a *target* or *goal*.
**Module**: An added feature that provides extra options for iptables, allowing for more extensive and complex traffic filtering rules.
**Table**: An abstraction in iptables that stores chains of rules. iptables includes the following tables: Security, Raw, NAT, Filter, and Mangle. Each table has a specific function, described below.

## iptables Tables
### Filter Table
The Filter table is the default table, using three chains: *OUTPUT*, *FORWARD*, and *INPUT*.

*INPUT*: Controls incoming connections. For instance, this might manage incoming SSH connections.
*FORWARD*: Manages incoming connections not directed to the local device, typically used on a router.
*OUTPUT*: Controls outgoing connections, such as navigating to a website using a browser.

### NAT Table
The NAT (Network Address Translation) table includes three chains: PREROUTING, POSTROUTING, and OUTPUT.

PREROUTING: Determines the destination IP address of a packet.
POSTROUTING: Alters the source IP address.
OUTPUT: Changes the target address of outgoing packets.

### Mangle Table
The Mangle table is used to modify packet IP headers.

### Raw Table
The Raw table provides a mechanism for marking packets to bypass connection tracking.

### Security Table
The Security table enables interaction with various OS security mechanisms, such as SELinux.

## iptables Rules
The rules in iptables are designed to control incoming and outgoing network traffic. Rules can also be used to configure port forwarding and create protocol-specific rules.

Each rule is made up of criteria and a target. The criteria of a rule are matched, and the specified actions are applied to the target object. If a packet doesn’t match a rule’s criteria, the next rule is processed. The decisions made by iptables are called actions. Below is a list of key actions for handling connections:

**ACCEPT**: Opens (allows) the connection.
DROP: Closes the connection without sending a response to the client.
**QUEUE**: Sends the packet to a queue for further processing by an external application.
**RETURN**: Returns the packet to the previous rule, stopping the processing of the current rule.
**REJECT**: Blocks the connection and sends an error message in response.
**DENY**: Drops the incoming connection without sending a response.
**ESTABLISHED**: Marks an already established connection, as the session has already received at least one packet

## iptables in practice

Display the current iptables configuration

```bash
$ sudo iptables --list
```

Show more details, incl. line numbers, size of processed packets, as well as IP addresses and port numbers in numeric format.

```bash
$ sudo iptables --line-numbers -L -v -n
```

## References

- https://hostman.com/tutorials/iptables-overview-and-practical-use/

