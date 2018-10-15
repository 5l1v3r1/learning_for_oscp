# nmap
quoted from the man pages.
## Description
Nmap (Network Mapper) is an open source tool for network exploration and security auditing. It was designed to rapidly scan large networks, although it works fine against single hosts. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services those hosts are offering, what operating systems they are running, what type of packet filters/firewalls are in use, and dozens of other characteristics. While Nmap is commonly used for security audits, many systems and network administrators find it useful for routine tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime.

The output from Nmap is a list of scanned targets, with supplemental information on each depending on the options used. Key among that information is the "interesting ports table" that table lists the port number and protocol, service name, and state. The state is either open, filtered, closed, or unfiltered. Open, means that an application on the target is listening for connection/packets on that port. Filtered, means that a firewall, filter, or other network obstacle is blocking the port so that Nmap cannot tell wheter it is open or closed 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MTUxNTc0NDksMTc5MzYxODQ0OCwtMj
A4ODc0NjYxMl19
-->