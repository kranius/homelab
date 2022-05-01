# Basic setup checklist of a routerOS v7 device

I recently bought a MikroTik router ([rb5009](https://mikrotik.com/product/rb5009ug_s_in)), here are the steps I followed for a simple home config. It's possible to run openWRT on such device but this document will focus on using routerOS v7.

Out of the box, your appliance should function as a simple router (NAT and dhcp). Plug your ISP box/modem into ether1 and your machine in one of ether2-8 (refer to the Quick Start guide of your hardware).

Of course this config is not sufficient, especially if you run your modem/box in bridge mode (IP on ether1 becomes your public IP)

## References :

- [official routerOS docs](https://help.mikrotik.com/docs/display/ROS/RouterOS)
- [official MikroTik forums](https://forum.mikrotik.com/)
- [official MikroTik youtube channel](https://www.youtube.com/mikrotik)
- [wikipedia](https://en.wikipedia.org/wiki/Internet_protocol_suite)


## Before anything :

- install [winbox](https://mikrotik.com/download) (works perfect under wine) as administration tool (possible to use shell but this document will focus on GUI)
- take your time, don't rush and misconfigure your appliance
- use `Safe Mode` : toggle in top left corner or side menu -> if connection drops system will revert changes after 9 minutes timeout

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

- __create new account__ : System > Users > click `+` and add a new user, rights = full, fill `Allowed Address` with your LAN IP
- __disable admin account__ : System > Users > click `x` after selecting old admin account
- __restrict MAC server__ : Tools > MAC server > click `MAC Telnet Server` > select `LAN` in dropdown (or create your own interface list in Interfaces > Interface List > do the same with `MAC Winbox Server`
- __disable other IP services__ : IP > Services > disable everything but winbox and ssh
- __change default ports__ : IP > Services > change SSH port to non default value (check your other firewalls and configs)
- __restrict services to LAN only__ : IP > Services > fill `Available From` field with privileged IP
-  __enable strong crypto__ : IP > SSH > check `enable strong crypto`

- __disable neighbor discovery__ : IP > Neighbors > Discovery Settings > select `none` as Interface
- __disable upnp__ : IP > UPnP > uncheck `Enabled`
- __disable bandwith server__ : Tools > BTest Server > uncheck `Enabled`
- __backup config__ : Files > Backup > fill `name` and `password`

##### Simple Networking

- __setup static leases__ : IP > DHCP Server > Leases > right click on IP then select `make static`
- __enable DNS over HTTPS__ : IP > DNS > choose master DNS, fill `DoH Server` and check `Verify DoH Certificate`
- __import DoH certificate__ : see [routerOS DNS docs](https://help.mikrotik.com/docs/display/ROS/DNS)
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
