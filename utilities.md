# Lesser known tools and arguments

###   [ss](https://www.man7.org/linux/man-pages/man8/ss.8.html) socket statistics

- -s --summary

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
- -t --tcp
- -u --udp
- -4 --ipv4

```
$ ss -4tu
Netid                State                Recv-Q                Send-Q                                  Local Address:Port                                   Peer Address:Port                 Process                
tcp                  ESTAB                0                     0                                      192.168.88.252:2442                                 192.168.88.251:49574                          
```

- -l --listening

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
