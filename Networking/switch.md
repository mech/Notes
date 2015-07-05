# Switch

Cisco 3750 StackWise

You can use various `show` commands to:

* Look at which interface is up or down, if down it is not going to pass on traffic.
* Look at the MAC address table of the switch to see what addresses has been learned.
* Check the port security.

```
switch#show version
Cisco IOS Software, c3750 software (c3750-ADVIPSERVICESK9-M), Version 12.2(44)SE1, RELEASE SOTWARE (fc1)

// Show current running configuration
Switch#show run

// Show interface
Switch#show ip int brief
Switch#show int fa 1/0/1

// MAC address table
Switch#show mac address-table

Switch#show mac address-table aging
Switch(config)#mac address-table static a820.6632.0087 vlan1 interface fa 1/0/1
```

* BIA - Burned in Address

Duplex mismatch? Look for high CRC errors.

## Virtual Switching System (VSS)

## Dynamic Multipoint VPN (DMVPN)

## RADIUS and AAA Security
