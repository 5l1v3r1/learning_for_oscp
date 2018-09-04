# Using Netcat for port scanning
The most basic form of command is:
`# nc [options] host port(s)`
options are described below
host can be either an IP address or valid hostname
Ports can be a single port or a range of ports such as 20-53 or individual ports separated by spaces.

### Let's get started
A small tool that can do remote port scanning would be nice to have and Netcat can fill this role very well and a lot of other ones.

A typical command to perform port scanning would be:
`# nc -v -w 3 -z 192.168.1.69 20-150`
The first portion of the command line that says: nc -v -w 3 which simply tells Netcat to give us more verbose feedback and to timeout after 3 seconds if no connections could be established.

The -z switch prevent Netcat from sending any data to a TCP connection and it will only send very limited data to a UDP connection.

Here is another example: you will use UDP protocol instead of the TCP protocol.
`# nc -v -w 3 -z -u 192.168.1.69 20-100`

### Using Netcat for banner grabbing
Another neat usage of Netcat is for banner grabbing(technique to glean information of the system on the Internet)
`# nc -v -n 192.168.1.69 80
GET HTTP`
Once connected above you simply issued the command: GET HTTP

### Combining both port scan and banner identification
Now we will combine both Port Scan and banner identification.
```bash
#echo GET HTTP | nc -v -n 216.58.199.228 80 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzgwOTA5NzQsMTE5OTI1Mzk3MCw5NDYwMj
IzMjMsMTM3Mjk4NjIwMF19
-->