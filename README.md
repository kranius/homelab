# My Homelab

My networking/devops/sysadmin skills were a bit dusty. Also a fun hobby.

## Current gear

#### Infra

- 1x [MikroTik rb5009]() running routerOS v7
- 2x [Xiaomi router 4a gigabit]() flashed with [openWRT]() (check instructions for flashing)
- 1x [Raspberry Pi 1 model B 512 MB]()
- 1x 2014 macbook pro (i5/8GB/256GB)
- 1x NAS (still deciding what should I get)

#### End

- User machines : multiple phones, tablets, laptops, pc/consoles
- IoT/Smart home stuff : TV

## Services

#### Exposed :

- Wireguard supporting roaming clients ("[road warrior]()" config) and hiding my IP behind a cheap VPS

#### DMZ :

- DNS filtering (running on the raspberry)
- DNS over HTTPS, terminated on the rb5009
- Container orchestration (I use the mbp to run non criticial services, basically my toy low-powered server)


#### LAN :

- Proper firewalling
- Wifi QoS
- Segregated IoT/smart stuff


## References

- [how to firewall (French gov)](https://www.ssi.gouv.fr/uploads/2018/01/guide_preconisations-pare-feux-zone-exposee-internet_anssi_pa_044_v1.pdf)
- [openWRT docs]()
- [routerOS docs]()
