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

In the third command I set the type to NS as I am interested in finding the nameservers for searching-eye.com. Type in the domain name as the fourth command and we get the corresponding nameservers for the domain searching-eye.com. Note that finding the nameservers can give us some information about the hosting provider of the domain. Some large organizations use their own nameservers e.g. ns2.google.com.

I now set the current server to one of the nameservers. this is because I am interested in finding the latest information about the domain. Note that querying from your own dns server may not give you the accurate information every time. I set the type to MX and again type in the domain name. What we get is a list of mail servers responsible for handling emails sent to that domain. The number before them denotes the priority with which to fetch mails. Lower the number, higher the priority.

Next I set the type to CNAME and type in a subdomain. I get a canonical name as infosecinstitute.com. This means any request to the queried domain (in this case prateek.searching-eye.com) will be redirected to infosecinstitute.com.

The ***dig*** command can be used to do same things.

### DNS Lookup and Reverse DNS Lookup
**DNS Lookup** Let's perform a DNS Lookup ourselves for infosecinstitute.com. We will do this by traversing the entire DNS hierarchy from the root servers to the top level domain. Open up the terminal and type in **dig**. You will get something as shown in the figure below
![resultofdig](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/dig.png)
What we get is a list of the DNS Servers. Let' use this root DNS server to query infosecinstitute.com. We do this as shown in the figure below.

![enter image description here](https://lh3.googleusercontent.com/krbck4w1l9USwjtO-hpNoQeBW1Pmztxd85P9w0Mfv2blSb_aZ0pY_reFzwk2x6OtYM5XqPeu5Jo "result")

The first block started with 'com.' shows the list of authoritative nameservers for the com domain. Notice the dot at the end, this is what makes this a fully qualified domain name (FQDN). 

The second block started with 'infosecinstitute.com.' shows the list of authoritative name servers for infosecinstitute.com.

And at last, we can see that the ip-address for infosecinstitute.com is 104.199.119.187

**Reverse DNS Lookup**-Performing Reverse DNS Lookup converts an IP-address into it's hostname. For this we need to write the IP-address in reverse order (for e.g. 192.168.1.1 will be 1.1.168.192) and then append ".in-addr.arpa." to it. Next we need to make a query for a PTR Record using DIG. Let's make a DNS PTR query for 216.92.251.5, the command here would be `dig 5.251.92.216.in-addr.arpa PTR`
![reverse look up](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/dig-reverse-lookup.png)

As we can clearly see, this ip-address resolves to infosecinstitute.com. As Simple as that!

### Understanding Wildcard Entries
**WildCard** - A wildcard entry is used to provide response for subdomains that do not exist. For e.g. let's say we have a domain example.com. If we set a wildcard record for *.example.com and give it the value example.com then the requests for all the non-existent subdomains of example.com (for e.g. abcd.example, blah.example.com) will point to example.com. In the information gathering stage of a penestration test of a website, it is important to identify the subdomains and the ip-addresses corresponding to them. Introducing a Wildcard feature reduces this to a small extent.

**Bypassing Wildcard entries** - In case wildcard entries are set on a particular domain, they could be bypassed to reveal information about it's subdomains. This is done by brute forcing the subdomains. We have a wordlist in which we contain the subdomain names we want to test the domain against. Then we do a ping of all these subdomains. if these domains resolve to an IP-address different than the host IP-address, then we can very surely say that this subdomain actually exists. However before performing a brute force it would be better to actually check if Wildcard entries are enabled or not. For that we can ping some random subdomains for e.g. 434234.example.com and see if it's IP-address is the same as the host IP-address(in this case example.com). If this is the case for some random subdomains, then we can clearly say that wildcard entries are enabled for this domain. We will perform a demo of this in the coming section.

### DNS Zone Transfer
We saw in the previous exercises that every domain has some authoritative name servers associated with it. For e.g. in the case of google.com , the name servers were ns1.google.com. These Nameservers are used for handling requests related to the domain google.com. Let's say we have a domain example.com and it has it's two nameservers as ns1.example.com and ns2.example.com. Usually a big organization will have more than one nameservers so that if one goes down for some time, the other one is ready to back it up and handle the requests. Usually one of these servers will be the Master server and the other one will be the slave server. Hence to stay in sync with each other. the slave server must query the Master server will provide the slave server with all the information it has. This is basically what is called a "Zone Transfer". It's like asking the nameserver "Give me everything you have". A properly configured nameserver should only be allowed to serve requests of Zone transfer from other Nameservers of the same domain. However if the server is not configured properly it will serve all requests of Zone transfer made to it without checking the querying client. This leads to leakage of valuable information. DNS Zone Transfer is sometimes referred through it's opcode mnemonic AXFR.

Let's see an example of a Zone transfer. We will be using the tool Fierce present by default in Backtrack. Fierce is one of the best tools available out there for DNS Analysis. Type in the following command `perl fierce.pl -dns searching-eye.com`. We get something as shown in the figure below.
![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/fierce-start-zone-transfer.png)

What fierce does is that it first finds out the nameservers for the domain. it then checks to see if they allow zone transfers. Since one of the nameservers is not properly configured. It allows zone transfer and what we see is a dump of all information 

#### Why is Zone Transfer a Security issue?
A zone transfer reveals a lot of information about the domain. This forms a very important part of the information gathering stage during a penestration test. vulnerability assessment etc. We can figure out a lot of things by looking at the dump. For e.g. we can find different subdomains. Some of them might be running on different servers. Those servers may not be fully patched and hence be vulnerable. From this point. we can start thinking about Metasploit ,Nessus, Nmap etc and do a full vulnerability assessment of the domain. Hence this kind of information increases our attack vector by a fair amount, an amount which cannot be ignored.

To protect your nameservers from leaking valuable information, one must allow zone transfer to other nameservers of the same domain only. For e.g. ns1.example.com should allow zone transfer to ns2.example.com only and discard all the other requests.

#### DNS Bruteforcing
DNS 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NzEyMjAxLDE5MjM0NjQ1MjcsLTI3NT
EwNzMxOSwxNjI1OTEzMzMxLDE0ODczNDQ2MTQsMTc0NDU3NjUz
LDIwMzc3MzYzNDAsNzIyMTE0MzQ2LDYwOTI4MjU5Myw3MTM4MT
E0ODMsLTE2OTIzNzcxNCwzNTY5MDYyOSw4ODgxMjYzMDQsNDMy
NzcwODk4LDQwNzQ4MjE0OCwtMjA4ODc0NjYxMl19
-->