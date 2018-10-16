# nmap
quoted from the man pages.
## Description
Nmap (Network Mapper) is an open source tool for network exploration and security auditing. It was designed to rapidly scan large networks, although it works fine against single hosts. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services those hosts are offering, what operating systems they are running, what type of packet filters/firewalls are in use, and dozens of other characteristics. While Nmap is commonly used for security audits, many systems and network administrators find it useful for routine tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime.

The output from Nmap is a list of scanned targets, with supplemental information on each depending on the options used. Key among that information is the "interesting ports table" that table lists the port number and protocol, service name, and state. The state is either open, filtered, closed, or unfiltered. Open, means that an application on the target is listening for connection/packets on that port. Filtered, means that a firewall, filter, or other network obstacle is blocking the port so that Nmap cannot tell whether it is open or closed. Closed, ports have no application listening on them, though they could open up at any time. Posts are classified as unfiltered, when they are responsive to Nap's probes, but Nmap cannot determine whether they are open or closed. Nmap reports the state combinations open|filtered. and closed|filtered. when it cannot determine which of the two states describe a port. The port table may also include software version details when version detection has been requested. When an IP protocol scan is requested (-s0), Nmap provides information on supported IP protocols rather than listening ports.

In addition to the interesting ports table, Nmap can provide further information on targets, including reverse DNS names, operating system guesses, device types, and MAC addresses.

A typical Nmap scan is shown in Example 1. The only Nmap arguments used in this example are -A, to enable OS and version detection, script scanning, and traceroute; -T4 for faster execution; and then the hostname.

Example 1.A representative Nmap scan
`nmap -A -T4 scanme.nmap.org`

## OPTIONS SUMMARY
summary is printed when Nmap is run with no arguments. It helps people remember the most common options, but is no substitute for the in-depth in the rest of this manual.  
I picked up options I think is often used.

- -sn: Ping Scan
- --dns-servers <server>: Specify custom DNS servers
- --traceroute: Trace hop path to each host
- -sU: UDP Scan
- -sN/sF/sX: TCP Null, FIN, and Xmas scans
- -sO: IP protocol scan
- -p <port ranges>: Only scan specified ports
- -r: Scan ports consecutively - don't randomize
- --top-ports <number>: Scan <number> most common ports
- -sV: Probe open ports to determine service/version info
- -O: Enable OS detection
- -T<0-5>: Set timing template (higher is faster)
- -D <decoy1>: Cloak a scan with decoys
- -S: Spoof source address
- --spoof-mac <mac address?: Spoof your MAC address
- -v: Increase verbosity level
- --open: Only show open ports
- -6: Enable IPv6 scanning
- -A: Enable OS detection, version detection, script scanning, and traceroute
- --privileged: Assume that the user is fully privileged
- -V: Print version number

## TARGET SPECIFICATION
Everything on the Nmap command-line that isn't an option is treated as a target host specification. The simplest case is to specify a target IP address or hostname for scanning.

Nmap supports CIDR-
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY2NzI4MjUzOCwxMjc5MTU1MTc3LC0yMz
M3Njg3NTEsLTE3MTgwNzQwMTksLTgyNDA4NDU4NiwxNzM2NDY5
OTg2LC0xMjQ5NzQ3ODI3LDQ2NzY2Mzc2NiwtMTM3NzU1ODIyOC
wxNzkzNjE4NDQ4LC0yMDg4NzQ2NjEyXX0=
-->