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
