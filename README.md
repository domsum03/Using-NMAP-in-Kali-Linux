
# Nmap Guide for Parrot OS on TryHackMe

## Introduction
Nmap (Network Mapper) is a powerful open-source network scanning tool used to discover hosts and services on a computer network. This guide will cover the basics of using Nmap on Parrot OS for TryHackMe activities.

## Table of Contents
- [Introduction](#introduction)
- [Basic Usage](#basic-usage)
- [Common Scan Types](#common-scan-types)
  - [Ping Scan](#ping-scan)
  - [Service Version Detection](#service-version-detection)
  - [Operating System Detection](#operating-system-detection)
  - [Aggressive Scan](#aggressive-scan)
- [Conclusion](#conclusion)
- [Additional Resources](#additional-resources)

## Common Scan Types
## Ping Scan
Discovers online hosts in the network without performing a port scan.

Example:

nmap -sn <target_ip>

## Service Version Detection
Detects the versions of services running on open ports.

Example:

nmap -sV <target_ip>

## Operating System Detection
Detects the operating system of the target host.

Example:

nmap -O <target_ip>

## Aggressive Scan
Performs a comprehensive scan, including OS detection, version detection, script scanning, and traceroute.

Example: 

nmap -A <target_ip>

## Next section we're going to use these techniques for a TryHackMe room Alfred (https://tryhackme.com/r/room/alfred)

Once in the room go ahead and start the machine and you should get an IP 
![Download OpenVPN Config](https://i.imgur.com/oF6od1v.png)

Also make sure you connect to OpenVPN to interact with the machine 

## First question asking How many ports are open? (TCP only)
![Download OpenVPN Config](https://i.imgur.com/T8ygBwh.png)

The NMAP scan I'm going to use is 
nmap -p- -T4 <target>
Here's what each part of the command does:

nmap: Calls the nmap tool.
-p-: Scans all 65,535 TCP ports.
-T4: Sets the timing template to 4, which makes the scan faster.
Replace <target> with the IP address or hostname of the target you want to scan. For example:

![Download OpenVPN Config](https://i.imgur.com/cegDLRw.png)

As we can see there's 3 TCP Ports open so we can answer the question 
![Download OpenVPN Config](https://i.imgur.com/bN9N5mw.png)

