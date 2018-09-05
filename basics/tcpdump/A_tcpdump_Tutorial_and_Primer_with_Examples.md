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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MDYxNDAyNjIsLTEwMzUxMjk4MSwxOT
Q3MjYzNDY2XX0=
-->