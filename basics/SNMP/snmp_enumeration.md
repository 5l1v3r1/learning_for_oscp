# SNMP Enumeration
quoted from [this site](https://www.greycampus.com/opencampus/ethical-hacking/snmp-enumeration)
SNMP (Simple Network Management Protocol) is an application layer protocol which uses UDP protocol to maintain and manage routers, hubs and switches other network devices on an IP network. SNMP is a very common protocol found enabled on a variety of operating systems like Windows Server, Linux & Unix servers as well as network devices like routers, switches etc.

SNMP enumeration is used to enumerate user accounts, passwords, groups, system names, devices on a target system.
It consists of three major components:
1. Managed Device: A Managed is a device or a host (technically known as a node) which has the SNMP service enabled. These devices could be routers, switches, hubs, bridges, computers etc.
2. Agent: An agent can be thought of as a piece of software that runs on a managed device. Its primary job is to convert the information into SNMP compatible format for the smooth management of the network using SNMP protocol.
3. Network Management System (NMS): These are the software systems that are used for monitoring of the network devices.

An agent running on every SNMP device will be providing access to a read and writable database. The database is referred to as the management information base (MIB) which is organized hierarchically and is a virtual database containing a formal description of all the network objects identified by a specific object identifier (OID) that can be managed using SNMP, It's a giant repository of values and settings. There is a manager involved in the process, and the manager will query the agent for various details.

Community strings is a text string used to authenticate communications between the management stations and network devices on which SNMP agents are hosted. Community Strings travel in clear text over the network, hence are subject to network sniffing attacks. Community Strings are sent with every network packet exchanged between the node and management station.

Two types of community strings:
1. Read only: This mode permits querying the device and reading the information, but does not permit any kind of changes to the configuration. The default community string for this mode is "public"
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMzQ5NDE4NjksMTk3MDgzNzYzNywtMT
I1NTA0MTY4XX0=
-->