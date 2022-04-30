# Lesser known tools and arguments

##   [ss](https://www.man7.org/linux/man-pages/man8/ss.8.html)

- -s, --summary

```
$ ss -s
Total: 163
TCP:   11 (estab 1, closed 0, orphaned 0, timewait 0)

Transport Total     IP        IPv6
RAW	  0         0         0        
UDP	  8         4         4        
TCP	  11        6         5        
INET	  19        10        9        
FRAG	  0         0         0        

```
- -t, --tcp
- -u, --udp
- -4, --ipv4

```
$ ss -4tu
Netid                State                Recv-Q                Send-Q                                  Local Address:Port                                   Peer Address:Port                 Process                
tcp                  ESTAB                0                     0                                      192.168.88.252:2442                                 192.168.88.251:49574                          
```

- -l, --listening

```
$ ss -4tul
Netid                State                 Recv-Q                Send-Q                               Local Address:Port                                      Peer Address:Port                Process                
udp                  UNCONN                0                     0                                          0.0.0.0:domain                                         0.0.0.0:*                                          
udp                  UNCONN                0                     0                                          0.0.0.0:bootpc                                         0.0.0.0:*                                          
udp                  UNCONN                0                     0                                          0.0.0.0:35447                                          0.0.0.0:*                                          
udp                  UNCONN                0                     0                                          0.0.0.0:mdns                                           0.0.0.0:*                                          
tcp                  LISTEN                0                     32                                         0.0.0.0:domain                                         0.0.0.0:*                                          
tcp                  LISTEN                0                     244                                        0.0.0.0:postgresql                                     0.0.0.0:*                                          
tcp                  LISTEN                0                     5                                        127.0.0.1:4711                                           0.0.0.0:*                                          
tcp                  LISTEN                0                     128                                        0.0.0.0:2442                                           0.0.0.0:*                                          
tcp                  LISTEN                0                     1024                                       0.0.0.0:http                                           0.0.0.0:*           
```

## [traceroute](https://www.man7.org/linux/man-pages/man8/traceroute.8.html)

- -I, --icmp
- -A, --as-path-lookups

```
$ traceroute -IA 1.1.1.1
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
 1  mkrouter (192.168.88.1) [*]  0.666 ms  0.605 ms  1.023 ms
 2  boxsfr (192.168.0.1) [*]  0.762 ms  0.678 ms  0.834 ms
 3  10.45.48.1 (10.45.48.1) [*]  32.296 ms  31.941 ms  34.694 ms
 4  sss1rj-ge-0-1-5.0.numericable.net (195.132.10.129) [AS21502]  37.845 ms  39.392 ms  39.167 ms
 5  ip-35.net-80-236-7.static.numericable.fr (80.236.7.35) [AS21502]  39.320 ms  39.127 ms  38.938 ms
 6  125.157.136.77.rev.sfr.net (77.136.157.125) [AS15557]  40.109 ms  34.963 ms  34.687 ms
 7  221.10.136.77.rev.sfr.net (77.136.10.221) [AS15557]  35.613 ms  35.422 ms  35.230 ms
 8  221.10.136.77.rev.sfr.net (77.136.10.221) [AS15557]  34.342 ms  27.744 ms  29.189 ms
 9  141.101.67.254 (141.101.67.254) [AS13335]  52.686 ms  52.497 ms  52.302 ms
10  one.one.one.one (1.1.1.1) [AS13335]  28.834 ms  28.598 ms  28.579 ms

```

## [ip](https://www.man7.org/linux/man-pages/man8/ip.8.html)

- a (shortcut for `addresss`)

```
 $ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether b8:27:eb:73:52:35 brd ff:ff:ff:ff:ff:ff
    inet 192.168.88.252/24 brd 192.168.88.255 scope global dynamic noprefixroute eth0
       valid_lft 457sec preferred_lft 382sec
    inet6 fe80::ba27:ebff:fe73:5235/64 scope link 
       valid_lft forever preferred_lft forever
```

- r (shortcout for `route`)

```
 $ ip r
default via 192.168.88.1 dev eth0 proto dhcp src 192.168.88.252 metric 202 
192.168.88.0/24 dev eth0 proto dhcp scope link src 192.168.88.252 metric 202 
```

## [netstat](https://www.man7.org/linux/man-pages/man8/netstat.8.html)

- -n, --numeric
- -t, --tcp
- -a, --all

```
$ netstat -nta
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2442            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:4711          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0     36 192.168.88.252:2442     192.168.88.251:51398    ESTABLISHED
tcp6       0      0 :::2442                 :::*                    LISTEN     
tcp6       0      0 :::5432                 :::*                    LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 ::1:4711                :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     

```

- -p --program (need root)

```
$ sudo netstat -ntap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:2442            0.0.0.0:*               LISTEN      373/sshd: /usr/sbin 
tcp        0      0 127.0.0.1:4711          0.0.0.0:*               LISTEN      562/pihole-FTL      
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN      404/postgres        
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      562/pihole-FTL      
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      509/lighttpd        
tcp        0    304 192.168.88.252:2442     192.168.88.251:51398    ESTABLISHED 9013/sshd: pi [priv 
tcp6       0      0 :::2442                 :::*                    LISTEN      373/sshd: /usr/sbin 
tcp6       0      0 :::5432                 :::*                    LISTEN      404/postgres        
tcp6       0      0 :::53                   :::*                    LISTEN      562/pihole-FTL      
tcp6       0      0 ::1:4711                :::*                    LISTEN      562/pihole-FTL      
tcp6       0      0 :::80                   :::*                    LISTEN      509/lighttpd       
```

## [ipcalc]()


```
$ ipcalc 192.168.0.1/24
Address:   192.168.0.1          11000000.10101000.00000000. 00000001
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.0.0/24       11000000.10101000.00000000. 00000000
HostMin:   192.168.0.1          11000000.10101000.00000000. 00000001
HostMax:   192.168.0.254        11000000.10101000.00000000. 11111110
Broadcast: 192.168.0.255        11000000.10101000.00000000. 11111111
Hosts/Net: 254                   Class C, Private Internet
```
