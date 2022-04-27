# Flashing OpenWRT on Xiaomi router 4a gigabit (no USB drive method)

### IMPORTANT :

As of writing (9 april 2022),
if your device uses EON memory chip EN25QX128, flashing will fail resulting in bricked hardware.
(check router-4a info link below to see which hardware revision you got).
Support is probably coming soon (?)



double check filenames, IP adresses, instructions
take your time and read the docs

for unbricking software & instructions, check openwrt infos (see below for link)



### References :

- [router-4a info](https://openwrt.org/inbox/toh/xiaomi/xiaomi_mi_router_4a_gigabit_edition)
- [OpenWRTInvasion](https://github.com/acecilia/OpenWRTInvasion)


### What you need :

- one xiaomi router 4a
- two ethernet cables (one is supplied in the package)
- one machine with
  1. ssh client
  2. python3
  3. openwrt firmware (download sysupgrade image, see [firmware selector](https://firmware-selector.openwrt.org/?version=21.02.2&target=ramips%2Fmt7621&id=xiaomi_mi-router-4a-gigabit))
  
### Setup and exploit :

- power the 4a
- connect your modem or ISP box into the WAN/Internet port of the the 4a
- connect your computer into one of the LAN ports
- open web browser, and go to adress 192.168.31.1
- follow instructions
- after you are logged in on router UI, your url will contain `stok=3700b146c87e45fea51170f87f47d34c`
- of course your value will be different, copy the part after `stok=`
- open terminal
- type `git clone https://github.com/acecilia/OpenWRTInvasion.git`
- type `cd OpenWRTInvasion`
- type `pip3 install -r requirements.txt`
- type `python3 remote_command_execution_vulnerability.py`
- follow instructions
- if everything went OK, you can now login with :
- type `ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -c 3des-cbc -o UserKnownHostFile=/dev/null root@192.168.31.1`
- username is `root` with password `root`
- you are now root on your xiaomi router 4a, time to install openwrt !


### OpenWRT installation :

- open another shell in the directory where you downloaded openwrt firmware (we assume you named it **firmware.bin**)
- get your ip on the xiaomi LAN, something like 192.168.31.x (check web UI or ifconfig)
- type `python3 -m http.webserver 8080`
- go back to root shell on the ssh session (or reconnect if needed)
- type `curl http://COMPUTER.LAN.IP.HERE/firmware.bin --output firmware.bin`
- type `sha256sum firmware.bin`
- verify if hash is the same as the one displayed on the firmware selector website (**important step**, if you get different hashes, redownload firmware)
- if hash is correct, you can now flash the firmware
- type `mtd -e OS1 -r write firmware.bin OS1`
- follow instructions
- shell will say device is rebooting, takes 5-10min don't poweroff or do stupid action
- open web browser and go to 192.168.1.1
- enjoy your OpenWRT
