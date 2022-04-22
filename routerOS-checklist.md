# Basic setup checklist of a routerOS v7 device

I recently bought a MikroTik router ([rb5009](https://mikrotik.com/product/rb5009ug_s_in)), here are the steps I followed for a simple home config. It's possible to run openWRT on such device but this document will focus on using routerOS v7.

Out of the box, your appliance should function as a simple router (NAT and dhcp). Plug your ISP box/modem into ether1 and your machine in one of ether2-8 (refer to the Quick Start guide of your hardware).

Of course this config is not sufficient, especially if you run your modem/box in bridge mode (IP on ether1 becomes your public IP)

## References :

- [official routerOS docs](https://help.mikrotik.com/docs/display/ROS/RouterOS)
- [official MikroTik forums](https://forum.mikrotik.com/)
- [official MikroTik youtube channel](https://www.youtube.com/mikrotik)
- [wikipedia references](https://en.wikipedia.org/wiki/Internet_protocol_suite#External_links)
- [Beej's guide to network programming](https://www.beej.us/guide/bgnet/) (center around C + GNU/Linux programming but very worth to read, esp chapters 2-3)

## Before anything :

- install [winbox](https://mikrotik.com/download) (works perfect under wine) as administration tool (possible to use shell but this document will focus on GUI)
- take your time, don't rush and misconfigure your appliance
- use `Safe Mode` : toggle in top left corner or side menu -> if connection drops system will revert changes after 9 minutes timeout
- ⚠️ __CHANGE DEFAULT ADMIN PASSWORD__ ⚠️ : System > Users > doubleclick on `admin` > Password

## If default config worked (you have internet access) :

Your machine should have IP 192.168.88.x/24 (default subnet, routerOS allocates IP down starting from upper bound)

Your MikroTik device has IP w.x.y.z/v on ether1 (requested via DHCP client)

Your MikroTik device has IP 192.168.88.1/24 on the `local` bridge or on a specific interface (via DHCP server)

Firewall has default ruleset and masquerade is activated.

##### Updating

- __update software__ : System > Packages > Check for update > choose `stable` channel and update
- __update firmware__ : System > Routerboard > Update
- __update CPU freq__ (rb5009 only ?) : System > Routerboard > Settings > choose `auto` for CPU frequency
- __reboot__ : System > Reboot
- __check CPU freq__ : System > Resources (on idle rb5009 it should be 350 MHz, 1400 MHz under load) 

##### Simple Security

- __restrict admin account__ :
- __restrict MAC server__ :
- __change default ports__ :
- __restrict services to LAN only__ :
-  __enable strong crypto__ : IP > SSH > check `enable strong crypto`
- __disable other IP services__ :
- __disable neighbor discovery__ :
- __disable upnp__ :
- __disable bandwith server__ :
- __enable disk logging__ :
- __backup config__ :

##### Simple Networking

- __setup static leases__ :
- __enable DNS over HTTPS__ :
- __setup VLAN__ :
- __enable wireguard__ :
- __backup config__ :

## If default config did not work or your routerOS device came in with blank config

##### Networking

- __reboot your pc__ :
- __networking fundamentals__ : [IPv4 / IPv6](https://help.mikrotik.com/docs/display/ROS/IPv4+and+IPv6+Fundamentals)
- __check this page__ : [first time guide](https://help.mikrotik.com/docs/display/ROS/First+Time+Configuration)


![troubleshooting](https://help.mikrotik.com/docs/download/attachments/328151/troubleshoot_if_ping_fails.jpg?version=1&modificationDate=1582275155077&api=v2)
(image credit @MikroTik)
