# TCP

https://www.youtube.com/watch?v=GP7uvI_6uas

#### Transmission Control Protocol (TCP)

If the Internet Protocol (IP) is thought as the protocol for getting information from a sending machine to a receiving machine, then *Transmission Control Protocol* (TCP) can be thought of as directing the transmitted packet to the correct program on the receiving machine.

As you might imagine, it is important to be able to identify both *where* the receiver is and *what* the packet is for, so TCP and IP are almost an inseperable pair: TCP/IP.

Each program/utility/service on a machine is assigned a *port number*. Coupled with and IP address, we can now uniquely identify a specific program on a specific machine.

The other thing that TCP is crucial for is *guaranteeing delivery* of packets, which IP alone does not do.

TCP does this by including information about how many packets the receiver should get, and in what order, and transmitting that information alongside the data.

Some ports ar eso commonly used that they have been standardized across all computers.

- FTP (file transfer) uses port **21**.
- SMTP (e-mail) uses port **25**.
- DNS uses port **53**.
- HTTP (web browsing) uses port **80**.
- HTTPS (secure web browsing) uses port **443**.

Steps of the TCP/IP process

1. When a program goes to send data, TCP break it into smaller chunks and communicates those packets to the computer's network software, adding a TCP layer onto the packet.
2. IP routes the individual packets from sender to receiver; this info is part of the IP layer surrounding the packet.
3. When the destination computer gets the packet, TCP looks at the header to see which program it belongs to; and since the routes packets take may differ, TCP also must present those packets to the destination program in the proper order.

5:22 youtube

if at any point along the way a router delivering information using the internet protocol *dropped* a packet, TCP would use additional information inside the headers to request that the sender pass along the extra packet so it could complete assembly.

After the packets have arrived, TCP ensures they are organized the correct order and can then be reassembled into the intended unit of data and delivered to the correct service.



