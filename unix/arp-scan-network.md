# Arp scanning with arp-scan

You can use `ARP(8)` to see what's on your arp cache but it is not always complete for the reason that you don't actively query for updating your ARP cache on your network. We can instead use `ARP-SCAN(1)` to scan the network for finding the information of hosts in your network.

```shell
$ arp-scan -l --interface eno1 # -l generates addresses from specified network interface config
192.168.169.1	c0:ea:e4:89:xx:xx	Sonicwall
192.168.169.20	ac:a3:1e:c3:xx:xx	(Unknown)
192.168.169.37	54:27:1e:b6:xx:xx	(Unknown)
```

`ARP-SCAN(1)` might not be available by default on your system. On Ubuntu, I had to install with the following command:

```shell
$ apt install -y arp-scan
```
