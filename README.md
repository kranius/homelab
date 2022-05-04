# My Homelab

Keeping my networking/devops/sysadmin skills up to date. Also a fun hobby.
Going for low cost/low power solutions if possible.

## Current gear

#### Infra

- 1x FTTLA 400/40 SFR modem
- 1x [MikroTik rb5009](https://mikrotik.com/product/rb5009ug_s_in) running routerOS v7 (see my [checklist](/routerOS-checklist.md))
- 2x [Xiaomi router 4a gigabit](https://www.mi.com/fr/mi-router-4a-gigabit-edition/specs) flashed with [openWRT](https://openwrt.org/) (check my [instructions](/openWRT-xiaomi4a.md) for flashing)
- 1x Raspberry Pi 1 model B 512 MB
- 1x 2014 macbook pro (i5/8GB/256GB)

#### End

- User machines : multiple phones, tablets, various laptops, pc/consoles (my main machine is a M1 Pro mbp)
- IoT/Smart home stuff : TV

#### Next purchases

- Moving everything to a safer & cleaner space (going rackmount seems overkill)
- Replacing the aging mbp with something beefier (currently looking at 1L thin clients such as [these](https://www.lenovo.com/us/en/c/desktops/thinkcentre/m-series-tiny) or [those](https://www.hp.com/us-en/shop/mlp/business-solutions/desktops-and-workstations))
- Upgrading the raspberry to a gen 4 (maybe one day they will be available again for a reasonable price)
- Better storage solution (looking to build a ZFS system or a Ceph cluster, maybe going for ~10 TB usable)

## Services

#### Exposed :

- Wireguard supporting roaming clients ("[road warrior]()" config) and hiding my IP behind a cheap VPS

#### DMZ :

- RADIUS auth server
- DNS over HTTPS, terminated on the rb5009 (I was running a Cloudflare tunnel on the rasp but I'm trying the feature on the MikroTik)
- USB storage as NFS (I don't need insane iops but it's starting to show it's age)
- Container orchestration (I use the mbp to run non criticial services, basically my toy low-powered server)

#### LAN :

- JellyFin
- Sonarr/Radarr
- HomeAssistant
- Network wide ad blocking (pihole)
- Double firewall architecture
- Wifi QoS
- 802.1X Dynamic VLAN
- Segregated L2/L3 for IoT/smart stuff and guest wifi

![dual fw diagram](/fu750903.jpg)

## TODO

- add wireguard tunnel from rasp to rb5009
- fix vlan configuration

## References

- [how to firewall (French gov)](https://www.ssi.gouv.fr/uploads/2018/01/guide_preconisations-pare-feux-zone-exposee-internet_anssi_pa_044_v1.pdf)
- [how to design a secure gateway (french gov)](https://www.ssi.gouv.fr/uploads/2020/06/anssi-guide-passerelle_internet_securisee-v3.pdf)
- [openWRT docs](https://openwrt.org/docs/start)
- [routerOS docs](https://help.mikrotik.com/docs/display/ROS/RouterOS)
- [lafibre.info](https://lafibre.info/) (french networking forum)
