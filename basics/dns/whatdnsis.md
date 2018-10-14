# DNS
DNS is a naming system for computers that converts human readable domain names into computer readable IP-addresses. Some security vulnerabilities exist due to misconfigured DNS nameservers that can lead to information disclosure about the domain. This forms an important step of the information gathering stage during a Penestration test or Vulnerability assessment. 

### DNS Basics
 DNS converts human readable domain names into IP-addresses. This is because domain names are much easier to remember than IP-addresses. This process may take place through a local cache or through a zone file that is present on the server. A zone file is a file on the server that contains entries for different resource records (RR). These records can provide us a bunch of information about the domain.
 So Let's understand how DNS resolution works. Let's say the user opens up the browser and types in infosecinstitute.com. It is now the responsibility of the DNS resolver in the user's operating system to fetch the IP address. It first checks it's local cache to see if it can find a record for the queried domain name. A cache usually contains a mapping of IP-addresses to hsotnames which are saved during recent lookups so that the resover does not have to fetch the IP address again and again. If it can't find the IP address in it's cache it queries the DNS server to see if it has a record for it. A DNS server is usually given to you by the ISP or you can manually set up a DNS server for yourself. If it still can't find the IP Address then it goes through a process or recursive DNS query in which it queries different nameservers to get the IP address of the domain. As soon as it finds the IP address it returns the IP address back to the user and also caches it for it's future use.
  Let's do a quick demo using 'nslookup' utility. Just type in the commands below.
  ```
  $ nslookup
  set type=a
  google.com
  ```
  In the second line we set the type = a. This means that we are querying for the A records which will return us an IP-address in return for the domain we query.

As soon as we type in google.com we get an output showing the server and an IP-address#port. This server is basically the current DNS server that will be serving our request. DNS uses UDP port 53 to serve its requests. We can also set the current DNS server by using the command "server ip-address"

Next line in the output shows "Non-authoritative answer". This basically means that our DNS server queried an external DNS server to fetch  the IP-Address. Below we can see all the IP-Address associated with google.com. This is usually the case with large organizations. They use multiple servers to serve the request as one server is generally not capable of handling all the requests.

### Resource Records and the Zone file
A Zone file is basically a text file present on the server hosting the domain that contains entries for different resource records. Each line is represented by a different record. In some cases these records may exceed one line and hence must be enclosed within a parentheses. Each zone file must start with a Start of Authority (SOA) records containing an authoritative nameserver for the domain and an email address of someone responsible for the management of the nameserver. An example of a zone file is given below.

$ORIGIN infosecinstitute.com.;This marks the beginning of the file
  $TTL	86400 ; TTL is 24 hours , it could also be 1d or 1h
  infosecinstitute.com  IN	 SOA ns1.infosecinstitute.com.	webmaster.infosecinstitute.com. (
            		2002026801 ; serial number of this zone file
            		2d ; refresh time for slave
            		5h ; retry time for slave
            		2w ; expiration time for slave
            		1h ; maximum caching time
            			     )
         NS                    ns1.infosecinstitute.com.       ; ns1 is a nameserver for infosecinstitute.com
         NS                    ns2.infosecinstitute.com.       ; ns2 is a backup nameserver for infosecinstitute.com
         MX                    10 mail.infosecinstitute.com.   ; mail server
  ns1     A                     192.168.1.1                    ; Ipv4 address for ns1.infosecinstitute.com
  www    CNAME                 infosecinstitute.com            ; www.infosecinstitute.com is an alias for infosecinstitute.com
  ftp    IN  CNAME             www.infosecinstitute.com.       ; CNAME for ftp
  mail   A                     192.0.3.2                       ; Ipv4 address for mail.infosecinstitute.com

As we can see that it contains a TTL value in the second line. this means that all the resource records have an expiration time of 1hr. after this time every record will have to make another query and refresh it's data.

We can also see the different records that are present in the zone file. The general way of writing a resource record is writing the domain name, record class, record type, and then some additional information.

Different types of Resource Records exist within a Zone file. However we are going to discuss some of the important ones.

- A Records - Maps an IP Address to a hostname 
	For e.g. 74.125. 236.890 for google.com
- NS Records-Delegates a given zone to use the given authoritative nameserver.
	For e.g. ns1.google.com is an authoritative nameserver for google.com
- MX Records-This basically tells us which server is responsible for receiving mails sent to that domain name.
- TXT Records-This consists of arbitrary human readable text in a record.
- CNAME Records-Gives an alias of one name to another.

Let's do a demo to make this clear.
![demo](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/nslookup-detail.png)

In the first command in nslookup I set the type to A which means I want IP-address for a particular domain. I type in the domain name as the second command and get the corresponding IP-address for it.

In the third command I set the type to NS as I am interested in finding the nameservers for searching-eye.com. Type in the domain name as the fourth command and we get the corresponding nameservers for the domain searching
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjE1NjM5MDcsNzEzODExNDgzLC0xNj
kyMzc3MTQsMzU2OTA2MjksODg4MTI2MzA0LDQzMjc3MDg5OCw0
MDc0ODIxNDgsLTIwODg3NDY2MTJdfQ==
-->