
**what is Path MTU Discovery?**\
It is dynamic discovery of the smallest MTU in the network path.\
Different links in a network path may have different MTUs.\
Sending packets larger than the smallest MTU causes fragmentation, which is inefficient.

**IPV4:**
1) Sender starts by sending packets with the "Don't Fragment (DF)" bit set.
2) If a router along the path has a smaller MTU, it drops the packet and sends back an ICMP "Fragmentation Needed" message.
3) The sender reduces the packet size and tries again.\
This continues until packets are small enough to pass through without fragmentation.

**IPV6**\
Routers do not fragment in IPV6. P MTU D is mandatory in IPV6.
