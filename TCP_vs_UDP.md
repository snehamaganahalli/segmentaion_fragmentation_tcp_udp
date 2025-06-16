TCP: length: 20 to 60B\
src port\
dst port

seq no\
ack no

header length\Data offset: Size of TCP header. 4 bits. (5 => 20B, 15=> 60B)\
Flags: SYN FIN ACK RST URG PSH\

window: receive window size. i.e. How much the receiver can accept the data.\
checksum:\
It is calculated on Pseudo hdr+TCP hdr+TCP body. Pseudo hdr(Its IP hdr part) = srcip + dstip + protocol (TCP,udp) + length TCP segment (TCP hdr + data length (MTU-IP-TCP)).\
urgent ptr

options
padding

====================================

UDP: 8 bytes fixed.

src port 2B (IP address half size)\
dst port 2B\
length: UDP hdr + data. In TCP only header length is there.
checksum: same like TCP.\
Pseudo hdr+UDP hdr+UDP body. Pseudo hdr(Its IP hdr part) = srcip + dstip + protocol (TCP,udp) + length UDP segment (UDP hdr + data length (MTU-IPhdr-UDPhdr)).

=======================================

TCP 3 way handshake:

If we only had:

Step 1: Client → SYN\
Step 2: Server → ACK\
Then the connection would be half-open. The server wouldn't know if the client received the ACK and is ready to communicate. This can lead to:

Unreliable connections
Resource waste (server holds resources for a client that may never respond)
Security vulnerabilities (e.g., SYN flood attacks), also suppose SYN comes twice because of delay and retransmission.

So we have SYN , SYN+ACK, ACK

Also to negotiate the syn numbers on both side.
Eg:
syn 1
               syn 11 +ack 2
ack (12)

=============================================================



===============================================











