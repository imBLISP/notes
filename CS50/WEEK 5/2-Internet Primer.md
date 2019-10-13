# INTERNET PRIMER

We've reached the point in the course where we beginthe transition away from the command-line oriented world of `C` and start considering the web-based world of `PHP` and the like.

Before we dive headlong into that world, it's a good idea to have a basic understanding of how humans and computers interact over the internet.

#### IP Adress

In order for your machine to uniquely identify itself on the internet, it needs an address.

- This way, it can send information out and also recieve information back to the correct location.

The addressing scheme used by computers is known as IP addressing.

`w.x.y.z`

Each of `w`, `x`, `y`, and `z` can be a nonnegative value in the range `[0, 255]`.

`123.45.67.89`

If each IP adress is 32 bits, that means there are roughly 4 billion addresses to give out.

The population of the world is somewhere in excess of 7 billion, and most folks in the western world have more than 1 device capable of internet connectivity.

- some workarounds have allowed us to deal with this problem (for now).

In recent years, we've been slowly phasing out this old scheme (IPv4) and replacing it with newer scheme (IPv6) that assigns computers 128-bit addresses, instead of 32-bit addresses.

instead of :`4,294,967,296`
we will use:`340,233,234,234,543,634,234,543,123,321,123,756,896`

#### IPv6 Address

`s:t:u:v:w:x:y:z`

Each of s, t, u, v, w, x, y, and z is represented by 1 to 4 hexadecimal digits in the range [0, ffff]. 

`2001:4860:4860:0:0:0:0:8844`
can also be represented as
`2001:4860:4860::8844`

#### DHCP

How do we get an IP address in the first place though? Surely we can't just choose any one we want. What if the want we want is already taken?

Somewhere between your computer and the internet at large exists a *Dynamic Host Configuration Protocol* (DHCP) server, whose role is to assign IP addresses to devices.

Prior to the widespread promulgation of DHCP, the task of assigning OP addresses fell to a system administrator, who would need to manually assign such addresses.

#### DNS

Odds are, you've never actually tried to visit a website by typing its IP address into you browser

The *Domain Name System* (DNS) exists to help us translate IP addresses to more memorable names that are more human-comprehensible.

In this way, DNS is somewhat like the yellow pages of the web.

|               Host                |  IPv4 Address   |
| :-------------------------------: | :-------------: |
|          Info.host1.net           |     0.0.0.0     |
|          Info.host2.net           |     0.0.0.1     |
|                                   |       ...       |
| Io-in-f138.1e100.net (google.com) | 74.125.202.138  |
|                                   |       ...       |
|         info.hostn-1.net          | 255.255.255.254 |
|          Info.hostn.net           | 255.255.255.255 |

Much like there is no yellow pages of the world, there is really no DNS record of the entire internet.

Rather, large DNS server systems (like Google's own) are more like aggregators, collecting smaller sets of DNS information and pooling them together, updating frequently.

In that way, large DNS server are like libraries that stock many different sets of local yellow page books. In order to have the most up-to-date phone numbers for businesses, libraries must update the books they have on hand.

DNS record sets are thus fairly decentralized.

#### Access Points

One of the ways we've dealt with the Ipv4 addressing problem is to start assigning multiple people to the same IP address.

The IP address is assigned to a *router*, whose job is to act as a traffic cop that allows data requests from all of the devices on you local network(your home or business, e.g.) to be processed through a single IP address.

Modern home networks consist of access points that combine a router, a modem, a switch, and other technologies together into a single device.

Modern business networks or large-scale wide-area networks (WAN's) still frequently have these as  separate devices to allow the size of their network to scale more easily. 

#### General

At home or at work we have local, small networks, and these networks are woven together to create a large, interconnected network-an internet.

- if you think about each of these small networks being isolated communities with only a single road in or out, the picture becomes bit clearer. 

