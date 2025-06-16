PDNTSPA: Physical layer, Data link layer, Network layer, Session , presentation, Application Layer.

Ethernet header:
src mac + dst mac + Ether type (IPV4/6) + FCS\
6+6+2+4 = 18\

Network Header:

IPV4:

Important fields:\
version: says v4 or v6\
Src IP\
Dst IP\
Protocol: UDP(17)/TCP(6)

Total length: including IP header\
IHL: 1byte(4 bits: 1111b = 15 => 4*15 = 60 B) IP header length  min:20 Max:60B. Becuase of this field you may have options, padding: both are variable. Fragment offset is multiplication of 8, here it is 4 \


Support fragmentation:\
Identification\
flags: DF/MF\
Fragment Offset

checksum: On the IP header

It will hop from 1 router to another:\
TTL

Qos:\
TOS

============================================================

IPV6:\
version\
src ip\
dst ip

payload length:(in V4 it was total length): Here it is only thepayload excluding the IPV6 header.
type/Next header: TCP/UDP\

No fragmentation support:\
It supports only src/dest fragmentation. Router should support the acceleration of the fragmentation packets.

TTL/Hop limit:

QOS\
Traffic class\
Flow label

No checksum

==================

Ethernet/data link layer: Frame: It includes the complete (eth-header+payload) = ETH hder + IP packet + FCS. (ethernet / wifi terminology)\
Network layer: Packet: IP headr = IP hdr + TCP/UDP segment\
Segment: TCP/UDP hdr + App data.





