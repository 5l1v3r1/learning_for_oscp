# DNS
DNS is a naming system for computers that converts human readable domain names into computer readable IP-addresses. Some security vulnerabilities exist due to misconfigured DNS nameservers that can lead to information disclosure about the domain. This forms an important step of the information gathering stage during a Penestration test or Vulnerability assessment. 

### DNS Basics
 DNS converts human readable domain names into IP-addresses. This is because domain names are much easier to remember than IP-addresses. This process may take place through a local cache or through a zone file that is present on the server. A zone file is a file on the server that contains entries for different resource records (RR). These records can provide us a bunch of information about the domain.
 So Let's understand how DNS resolution works. Let's say the user opens up the browser and types in infosecinstitute.com. It is now the responsibility of the DNS resolver in the user's operating system to fetch the IP address. It first checks it's local cache to see if it can find a record for the queried domain name. A cache usually contains a mapping of IP-addresses to hsotnames which are saved during recent lookups so that the resover does not have to fetch the IP address again and again. If it can't find the IP address in it's cache it queries the DNS server to see if it has a record for it. A DNS server is usually given to you by the ISP or you can manually set up a DNS server for yourself. If it still can't find the IP Address then it goes through a process or recursive DNS query in which it queries different nameservers to get the IP address of the domain. As soon as it finds the IP address it returns the IP address back to the user and also caches it for it's future use.
  Let's do a quick demo using 'nslookup' utility. Just type in the commands below.
  ```
  $ nslookup
  set type=a
  google.com```
  In the second line we set the type = a. This means that we are querying for the A records which will return us an IP-address in return for the domain we query.

As soon as we type in google.com we get an output showing the server and an IP-address#port. This server is basically the current DNS server that will be serving our request. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE4NDg3NDE0LC0yMDg4NzQ2NjEyXX0=
-->