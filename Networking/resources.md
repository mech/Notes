# Resources

* [iPhone and Wireshark](http://stackoverflow.com/questions/1598407/iphone-and-wireshark)
* [Building a graphics card for the Internet](https://imgix.exposure.co/building-a-graphics-card-for-the-internet)

## Ethernet

10Mbps (1980), 100Mbps (Fast Ethernet, 1995), 1000Mbps (1Gbps, 1999), 10 Gigabit (2002), 40 Gigabit and 100 Gigabit (2010).

Timeline:

* 1960 - Packet switching used by ARPANET
* 1973 - Vint Cerf and Bob Kahn wrote the TCP specification making use of packet switching
* 1980 - Twisted-pair replacing coaxial cable

Connectionless protocols:

* Ethernet
* Internet Protocol (IP)
* User Datagram Protocol (UDP)

Connection-oriented protocols:

* X.25
* Frame Relay
* Multiprotocol Label Switching (MPLS)
* Transmission Control Protocol (TCP)

Until the introduction of Ethernet switches, half-duplex (CSMA/CD, MAC) was the typical mode of operation for Ethernet devices. However, these days almost all Ethernet devices are connectedly directly to a port on a switch that is operating in full-duplex mode and CSMA/CD protocol is shut off.

## Switch

Smarter than Hub. Switch is a directory of MAC addresses.
A fresh switch do not have the correct directory. So all nodes will tell the switch their MAC address to help it populate the directory.

Layer 2 (Data Link layer) address is MAC address.


## Router

Router is a directory of IP addresses.

Layer 3 (Network layer)

## VLAN

Logical LAN which contain it's own broadcast domain.
Must be in the same subnet.

You need a layer 3 device to communicate between VLANs.