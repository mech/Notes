# Resources

* [iPhone and Wireshark](http://stackoverflow.com/questions/1598407/iphone-and-wireshark)
* [Building a graphics card for the Internet](https://imgix.exposure.co/building-a-graphics-card-for-the-internet)

## Ethernet

Developed by Xerox for talking to printers. Competitors are TokenRing, LocalTalk,

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

## Switch - Layer 2 (Data Link Layer)

Learn MAC address and make forwarding decision. You can connect switch to another switch. Physical addressing.

Smarter than Hub but more intelligent as in making forwarding decision. Switch is a directory of MAC addresses.
A fresh switch do not have the correct directory. So all nodes will tell the switch their MAC address to help it populate the directory.

MAC address is 6 bytes (48 bits). First 3 bytes is the vendor code, the Organisationally Unique Identifier (OUI). The last 3 bytes is assigned by the vendor.

A switch port can have multiple MAC addresses. Each port on the switch represent it's own collision domain. Since there is no possibility of collision, then it can have full duplex mode. No more CSMA also.

Layer 2 (Data Link layer) address is MAC address.

PDU - Frame

Use serial port for COM interface, but now a lot of modern switch has USB or mini-USB.

**Frame forwarding options (Egress)**:

* Cut-through switching - As soon as the switch see the 48-bit MAC destination part and start forward the frame immediately. It does not interrogate the check sequence to check for frame error. Very popular in data-center.
* Store-and-forward switching - Receive the entire frame and look at Frame Check Sequence (FCS) to ensure valid frame. Don't waste bandwidth but is slower.
* Fragment-free switching - First 64 bytes, look at Ether Type, Source MAC and Dest MAC. No FCS.

**Enable Default Gateway**

```
switch>enable
switch#
switch(config)#ip default-gateway 192.168.1.1
switch(config)#end
```

## Router

Router is a directory of IP addresses. Logical addressing. Packet Switching.

Router will separate broadcast domain. It will not forward broadcast traffic (FFFF.FFFF.FFFF).

Layer 3 (Network layer)

PDU - Packet, Datagrams

Router can dynamically learn the logical addresses using BGP, OSFP, etc.

Default route like 0.0.0.0/0 manually entered?

## VLAN

Logical LAN which contain it's own broadcast domain.
Must be in the same subnet.

You need a layer 3 device to communicate between VLANs.