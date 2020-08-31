![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of shame (2020-08-31)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.220.101.9|-|10
185.129.62.62|tor01.zencurity.dk|10
51.15.43.205|tor4thepeople3.torexitnode.net|9
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|9
77.247.181.165|politkovskaja.torservers.net|9
80.67.172.162|algrothendieck.nos-oignons.net|9
185.220.101.8|-|8
51.75.64.187|relay4.tor.ian.sh|8
195.254.135.76|-|8
94.102.51.78|vps1.torrentflame.org|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
51.77.135.89|ns31066279.ip-51-77-135.eu|8
209.141.45.189|tor2.friendlyexitnode.com|8
51.83.139.55|ip55.ip-51-83-139.eu|8
207.244.70.35|-|8
171.25.193.25|tor-exit5-readme.dfri.se|8
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|8
51.75.52.118|ns3130898.ip-51-75-52.eu|8
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|8
51.195.166.192|ip192.ip-51-195-166.eu|8
51.195.148.18|relay2.tor.ian.sh|8
185.220.101.207|-|8
51.158.111.157|157-111-158-51.instances.scw.cloud|8
162.247.74.200|kiriakou.tor-exit.calyxinstitute.org|7
162.247.74.204|billsf.tor-exit.calyxinstitute.org|7
54.36.108.162|ns3112521.ip-54-36-108.eu|7
185.117.215.9|tor3.digineo.de|7
142.44.246.156|156.ip-142-44-246.net|7
54.38.81.231|ns31251136.ip-54-38-81.eu|7
212.47.229.4|-|7
217.182.192.217|ns3073700.ip-217-182-192.eu|7
171.25.193.77|tor-exit1-readme.dfri.se|7
171.25.193.78|tor-exit4-readme.dfri.se|7
192.42.116.13|this-is-a-tor-exit-node-hviv113.hviv.nl|7
198.251.89.80|tor-exit-01.nonanet.net|7
185.165.168.229|-|7
166.70.207.2|this.is.a.tor.node.xmission.com|7
185.220.102.8|185-220-102-8.torservers.net|7
89.234.157.254|marylou.nos-oignons.net|7
51.15.106.64|64-106-15-51.instances.scw.cloud|7
193.218.118.131|131.118.218.193.urdn.com.ua|7
185.220.101.215|-|7
185.220.101.216|-|7
162.247.74.27|turing.tor-exit.calyxinstitute.org|7
51.83.139.56|ip56.ip-51-83-139.eu|7
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|7
51.83.69.84|welcome-europe.website|7
145.239.82.87|relay10f.tor.ian.sh|7
171.25.193.20|tor-exit0-readme.dfri.se|7
62.102.148.69|-|7
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|7
185.220.102.251|tor-exit-relay-5.anonymizing-proxy.digitalcourage.de|7
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|7
35.0.127.52|tor-exit.eecs.umich.edu|7
51.68.139.151|151.ip-51-68-139.eu|7
149.56.99.85|85.ip-149-56-99.net|7
77.247.181.163|lumumba.torservers.net|7
54.39.16.73|ns555166.ip-54-39-16.net|7
193.218.118.130|130.118.218.193.urdn.com.ua|7
145.239.92.26|relay3.tor.ian.sh|7
192.42.116.27|this-is-a-tor-exit-node-hviv127.hviv.nl|7
45.154.35.251|tor-exit-1.darkdata.to|7
104.244.79.241|lux.tor.stevencampbell23|7
162.247.73.192|-|7
185.220.101.16|-|7
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|7
185.220.101.205|-|7
185.220.101.203|-|7
23.160.208.245|relay13f.tor.ian.sh|7
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|7
185.100.87.206|geri.enn.lu|7
