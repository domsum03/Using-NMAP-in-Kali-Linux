
# Nmap Guide for Parrot OS on TryHackMe

## Introduction
Nmap (Network Mapper) is a powerful open-source network scanning tool used to discover hosts and services on a computer network. This guide will cover the basics of using Nmap on Parrot OS for TryHackMe activities.

## Table of Contents
- [Introduction](#introduction)
- [Basic Usage](#basic-usage)
- [Common Scan Types](#common-scan-types)
  - [Ping Scan](#ping-scan)
  - [Port Scan](#port-scan)
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
