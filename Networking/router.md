# Router

L3 device. Not many ports. Divide boundary.

**From user mode to privilege mode**

```
Router>
Router>enable
Router#
```

**Go into configuration mode**

```
Router#config terminal
Router(config)#
Router(config)#interface fastethernet 0/0
Router(config-if)#
```

**Secure router**

```
Router(config)#line console 0
Router(config-line)#password cisco_123
Router(config-line)#login
Router(config-line)#end

Router(config)#line aux 0
Router(config-line)#password cisco_456
Router(config-line)#login

Router(config)#line vty 0 4
Router(config-line)#password cisco_789
Router(config-line)#login
```

