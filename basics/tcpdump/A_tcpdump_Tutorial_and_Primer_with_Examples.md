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



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTU1NDIzNTksLTEwMzUxMjk4MSwxOT
Q3MjYzNDY2XX0=
-->