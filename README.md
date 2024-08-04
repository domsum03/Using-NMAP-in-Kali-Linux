
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

We're going to gather additional information such as the operating system and version

Using nmap with the -A and -sV options provides a comprehensive scan that includes detailed information about the operating system, service versions, and more. Here is the breakdown of the command:

nmap -A -sV <target>
Here's what each part of the command does:

nmap: Calls the nmap tool.
-A: Enables OS detection, version detection, script scanning, and traceroute.
-sV: Probes open ports to determine service/version information.
For example:

nmap -A -sV <target_ip>

![Download OpenVPN Config](https://i.imgur.com/x9CADcT.png)

## Explanation of Options
-A: This option activates OS detection, version detection, script scanning, and traceroute.

OS Detection: Tries to identify the operating system of the target machine.
Script Scanning: Runs a set of default scripts against the target to gather additional information.
Traceroute: Identifies the path packets take to reach the target.

-sV: This option enables version detection.

Service/Version Detection: Tries to determine the version of the services running on open ports. This includes gathering banner information and comparing it against a database of known service versions.

Benefits of Combining -A and -sV
Combining these options in a single scan allows you to gather extensive information about the target, which is valuable for various purposes:

##  Comprehensive Security Assessment:

Vulnerability Identification: Knowing both the OS and specific versions of services helps identify vulnerabilities unique to those systems and applications.

Patch Management: Helps ensure that all software versions are up to date with the latest security patches.

Asset Management: Detailed version information aids in maintaining an accurate inventory of network assets.

Compliance: Ensures that all systems are compliant with security policies and regulations.

Targeted Exploits: Detailed information allows penetration testers to craft more targeted attacks.

Weakness Identification: Identifies outdated or misconfigured services that could be exploited.


## Output of command nmap -A -sV 
![Download OpenVPN Config](https://i.imgur.com/1us5OwU.png)

### Port 80 (Web Server)
- **Service**: Microsoft IIS version 7.5
- **Details**:
  - Supports risky methods like TRACE
  - Site doesn't have a title set

### Port 3389 (Remote Desktop)
- **Service**: Microsoft Remote Desktop
- **Details**:
  - SSL certificate for "alfred", valid until February 2025
  - System name and domain: "ALFRED"
  - Running Windows

### Port 8080 (Web Server)
- **Service**: Jetty version 9.4
- **Details**:
  - Site doesn't have a title
  - One disallowed entry in the robots.txt file

## Additional Information
- **Clock Skew**: The target's time is slightly off by about 2-3 seconds from the scanner’s time.


- Three open ports were found with specific services running on them.
- The target is likely running a version of Windows.
- This information can help in assessing the security and configuration of the target.

# Potential Risks Based on Nmap Scan Results

## Overview
A hacker could exploit the information from the `nmap` scan to target vulnerabilities and weaknesses in the system.

## Port 80 (Microsoft IIS 7.5)
- **Risks**:
  - **TRACE Method**: Exploit for cross-site tracing attacks.
  - **Known Vulnerabilities**: Use exploits targeting older IIS versions.

- **Actions**:
  - **Directory Traversal**: Access restricted files.
  - **Remote Code Execution**: Run malicious code.

## Port 3389 (Microsoft RDP)
- **Risks**:
  - **Brute Force**: Guess RDP credentials.
  - **Exploits**: Target specific RDP vulnerabilities (e.g., BlueKeep).

- **Actions**:
  - **Unauthorized Access**: Gain remote control.
  - **Data Theft**: Steal sensitive information.

## Port 8080 (Jetty 9.4)
- **Risks**:
  - **Server Vulnerabilities**: Exploit Jetty-specific issues.
  - **Misconfiguration**: Access due to weak settings.

- **Actions**:
  - **Injection Attacks**: Exploit web application flaws.
  - **Service Enumeration**: Identify and exploit services.

## Additional Risks
- **SSL Certificate**: Use for phishing attacks.
- **Clock Skew**: Minor time differences could assist in certain attacks.

## Summary
The scan information helps hackers identify and exploit system vulnerabilities, gain unauthorized access, and perform targeted attacks. Securing services, updating software, and using strong authentication are essential to mitigate these risks.

## Next post we're going to work on completeing the Alfred room.
