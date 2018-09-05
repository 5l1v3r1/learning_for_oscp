# A tcpdump Tutorial and Primer with Examples

## Index
- [Why_tcpdump](#whytcpdump)
- [Basics](#basics)
- [Basic Examples](#basicexamples)
	- [Basic communication](#basiccommunication)
	- [Find_Traffic_By_IP](#findtrafficbyip)
	- [Filter_By_Source_And/Or_Destination](#filterbysourceandordestination)
	- [Show_Traffic_By_Network](#showtrafficbynetwork)
	- [Show_Traffic_By_Port](#showtrafficbyport)
	- [Show_Traffic_By_Protocol](#showtrafficbyprotocol)
	- [Show_IPv6_Traffic](#showipv6traffic)
	- [Find_Traffic_Using_Port_Ranges](#findtrafficusingportranges)
	- [Find_Traffic_Based_On_Packet_Size](#findtrafficbasedonpacketsize)
	- [Writing_To_A_File](#writingtoafile)
- [Advanced_Examples](#advancedexamples)
	- [Isolate_Tcp_Flags](#isolatetcpflags)
	- [Find_Http_User_Agents](#findhttpuseragents)
	- [Find_Cleartext_Http_Gets](#findcleartexthttpgets)
	- [Find_Http_Hosts](#findhttphosts)
	- [Find_Http_Cookies](#findhttpcookies)
	- [Find_Ssh_Connections](#findsshconnections)
	- [Find_Dns_Traffic](#finddnstraffic)
	- [Find_Ftp_Traffic](#findftptraffic)
	- [Find_Cleartext_Passwords](#findcleartextpasswords)
	- [Find_Packets_With_Evil_Bit](#findpacketswithevilbit)
	- [Summary](#summary)

## <a id="whytcpdump">Why tcpdump?</a>
Tcpdump is the premier network analysis tool for information security professionals. Having a solid grasp of this uber-powerful application is mandatory for anyone desiring a thorough understanding of TCP/IP. Many prefer to use higher level analysis tools such as Wireshark, but I believe this to usually be a mistake.

When using a tool that displays network traffic a more natural way the burden of analysis is placed directly on the human rather than the application. This approach cultivates continued and elevated understanding of the TCP/IP suite, and for this reason I strongly advocate using tcpdump instead of other tools whenever possible.

## <a id="basics">Basics</a>
Below are a few options you can use when configuring tcpdump. They're easy to forget and/or confuse with other types of filters, e.g., Wireshark, so hopefully this page can serve as a reference for you, as it does me. Here are the main ones I like to keep in mind depending on what I'm looking at.

### *Options*
- **-i any**: Listen on all interfaces just to see if you're seeing any traffic.
- **-i eth0**: Listen on the eth0 interface.
- **-D**: Show the list of available interfaces
- **-l**: Line-readable output (for viewing as you save, or sending to other commands)
- **-A**: Display output in ASCII
- **-n**: Don't resolve hostname
- **-nn**: Don't resolve hostname or port names.
- **-q**: Be less verbose (more quiet) with your output.
- **-t**: Give human-readable timestamp output.
- **-tttt**: Give maximally human-readable timestamp output.
- **-X**: Show the packet's contents in both HEX and ASCII
- **-XX**: Same as -X, but also shows the ethernet header.
- **-v, -vv, -vvv**: Increase the amount of packet information you get back
- **-c**: Only get x number of packets and then stop
- **-s**: Define the snaplength (size) of the capture in bytes. Use -s0 to get everything, unless you are intentionally capturing less.
- **-S**: Print absolute sequence numbers.
- **-e**: Get the ethernet header as well.
- **-q**; Show less protocol information.
- **-E**: Decrypt IPSEC traffic by providing an encryption key

### *Expressions*
In tcpdump, Expressions allow you to trim out various types of traffic and find exactly what you're looking for. Mastering the expressions and learning to combine them creatively is what makes one truly powerful with tcpdump.

There are three main types of expression: ***type***, ***dir***, and ***proto***.
- Type options are: **host**, **net**, **port**
- Direction lets you do **src**, **dst**, and combinations thereof.
- Proto(col) lets you designate: **tcp**, **udp**, **icmp**, **ah**, and many more.

## <a id="basicexamples">Examples</a>
So, now that we've seen what our options are, let's look at some real-world examples that we're likely to see in our everyday work.

### <a id="basiccommunication">Basic Communication</a>
Just see what's going on, by looking at all interfaces.
```bash
# tcpdump -i any
```

### Specific interface
Basic view of what's happening on a particular interface.
```bash
# tcpdump -i eth0
```

### Raw Output View
Verbose output, with no resolution of hostname or port numbers, absolute sequence numbers, and human-readable timestamps.
```bash
# tcpdump -ttttnnvvS
```

### <a id="findtrafficbyip">Find Traffic by IP</a>
One of the most common queries, this will show you traffic from 1.2.3.4, whether it's the source or the destination.
```bash
# tcpdump host 1.2.3.4
```

### Seeing more of the packet with hex output
Hex output is useful when you want to see the content of the packets in question, and it's often best used when you're isolating a few candidates for closer scrutiny.
```bash
# tcpdump -nnvXSs 0 -c1 icmp
```

### <a id="filterbysourceandordestination">Filtering by source and destination
It's quite easy to isolate traffic based on either source or destination using **src** and **dst**
```bash
# tcpdump src 2.3.4.5
# tcpdump dst 3.4.5.6
```

### <a id="showtrafficbynetwork">Finding packets by network</a>
To find packets going to or from a particular network, use the **net** option. You can combine this with the **src** or **dst** options as well.
```bash
# tcpdump net 1.2.3.4/24
```

### <a id="showtrafficbyport">Show traffic related to a specific port</a>
You can find specific port traffic by using the **port** option followed by the port number.
```bash
# tcpdump port 3389
```

### <a id="showtrafficbyprotocol">Show traffic of one protocol</a>
If you're looking for one particular kind of traffic, you can use tcp, udp, icmp, and many others as well.
### <a id="showipv6traffic">Show only IP6 traffic</a>
You can also find all IP6 traffic using the protocol option.
```bash
# tcpdump ip6
```

### <a id="findtrafficusingportranges">Find Traffic Using Port Range</a>
You can also use a range of ports to find traffic.
```bash
# tcpdump portrange 21-23
```

### <a id="findtrafficbasedonpacketsize">Find Traffic based on packet size</a>
If you're looking for packets of a particular size you can use these options. You can use less, greater, or their associated symbols that you would expect from mathematics.
```bash
# tcpdump less 32
# tcpdump greater 64
# tcpdump <= 128
```

### <a id="writingtofile">Reading / Writing captures to a file</a>
It's often useful to save packet captures into a file for analysis in the future. These files are known as PCAP (PEE-cap) files, and they can be processed by hundreds of different applications, including network analyzers, intrusion detection systems, and of course by tcpdump itself. Here we're writing to a file called capture_file using the -w switch.
```bash
# tcpdump port 80 -w capture_file
```
You can read PCAP files by using the **-r** switch. Note that you can use all the regular commands within tcpdump while reading in a file; you're only limited by the fact that you can't capture and process what doesn't exist in the file already.
```bash
# tcpdump -r capture_file
```

## <id="advancedexamples"></a>
Now that we've seen what we can do with the basics through some examples, let's look at some more advanced stuff.

### <a id="findhttpuseragents"></a>
### <a id="findcleartexthttpgets"></a>
### <a id="findhttphosts"></a>
### <a id="findhttpcookies"></a>
### <a id="findsshconnections"></a>
### <a id="finddnstraffic"></a>
### <a id="findftptraffic"></a>
### <a id="findcleartextpasswords"></a>
### <a id="findpacketswithevilbit"></a>
### <a id="summary"></a>

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTM5ODIzNDQ4LC0xOTA2MTQwMjYyLC0xMD
M1MTI5ODEsMTk0NzI2MzQ2Nl19
-->