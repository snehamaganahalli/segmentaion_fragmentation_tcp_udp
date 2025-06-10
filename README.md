# segmentaion_fragmentation_tcp_udp

**Segmentation vs Fragmentation**

1) Segmenation happens in TCP/Transport layer. Fragmentation happens in IP layer. \
   Segmentation is only TCP concept. IN UDP segmentation is not present.

   **What is TCP segmentation?** \
   Dividing the large data from the application layer into smaller segments/pieces at the transport layer is called segmentation.\
   This is to ensure that transport layer can handle it efficientl within its limit of supporting the max segment size.

   MSS = MTU - (TCP + IP header) = MTU - (20+20) = MTU - 40.\
   MSS = 1500 -40 = 1460

   Each segment will have a TCP header and Each fragment will have IP header.

**What is Fragmentation?**\
Fragmentation is IP layer/network layer concept. If the packet size > 1500 i.e. MTU, then fragmentation takes place.\
These fragments are reassembled at the destination.

1) When we speak about fragmentation. Only UDP IPv4 supports it. TCP does not supports fragmentation because it has MSS to adjust.\
   IPV6 routers does not support segmentation. if a packet of greater MTU size is sent then, ICMP response is sent to send the lower MTU packet and the packet is dropped.\
   Only source/destination(end points) fragmentation is supported in IPV6.\

   Similarity: both the segment reassembly and fragment reassembly is at the destination.

**Segment size > MTU ==>	Fragmentation or drop (ICMP error) ==>	Inefficient**\
Eg: TCP segment is 3000 and MTU is 1500 => make 2 frags of 1500 and 1500

**Segment size < MTU ==>	Sent as-is ==>	Efficient and preferred**\
TCP segment size is 1460 => no fragmentation

=======================\
Let’s walk through what happens when:

Application data = 6000 bytes\
MTU = 2000 bytes\
MSS = MTU - 40 = 1960.

**segmentation:**\
APP data/MSS = 6000/1960 = 3.06\
1960 * 3 = 5880 => 6000 -5880 = 120\
segment 1 (s1) : 2000-40 = 1960\
S2 = 1960\
S3 = 1960\
S4 = 120\

**MTU is 2000 and all the segments are within MTU so no fragmentation is done.\
The Maximum Segment Size (MSS) is determined during the TCP three-way handshake and is based on the Maximum Transmission Unit (MTU) of the underlying network.**\

================================

**When fragmentation takes place?**\
DF bit should be 0

**How to identify the fragments of the same packet**\
The Identification field is a 16-bit field in the IPv4 header used to uniquely identify fragments of an original IP packet.\
Identification filed in the IP header will be same for all the fragments.

MF bit (More Fragment filed) will be 1 for all frgs except last one.

Fragment offset (FO) field is used reassemble the packet. It tells in which position the fragment belongs in the packet.\
FO field is 13 bit. Therefore you can store upto 2^13 -1 (including 0) = 8191 B. Since this filed is multiple of 8 bytes. It becomes 8191*8=65528 B.

**Reassembly:**\
Always reassembly happens at the end points and never by the routers.

Eg:
4000 B (MSS + TCP header) of data is fragmented as below. MTU is 1500\
F1 (fragment1): 1480 => Starting byte: 0 => FO: 0\
F2: 1480 =>                 1480 => FO = 1480/8 = 185\
F3: 1440 =>                 2690 => FO = 2690/8 = 370

=
