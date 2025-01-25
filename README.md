![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

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
ipset -q create ipsum hash:ip
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2025-01-25)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
194.0.234.37|-|10
194.0.234.38|-|10
80.82.77.139|dojo.census.shodan.io|8
2.57.122.192|-|8
83.222.191.62|-|8
92.118.39.73|-|8
92.118.39.74|-|8
92.255.85.188|-|8
92.255.85.189|-|8
102.211.152.45|45.152.211.102.angolacables.ao|8
167.94.145.99|-|8
193.32.162.130|-|8
193.32.162.132|-|8
193.32.162.134|-|8
193.32.162.139|-|8
218.92.0.112|-|8
218.92.0.219|-|8
218.92.0.231|-|8
37.58.18.237|-|8
96.67.59.65|-|8
80.82.77.33|sky.census.shodan.io|7
82.200.65.218|gw-bell-xen.ll-nsk.zsttk.ru|7
2.57.122.186|-|7
2.57.122.189|-|7
2.57.122.190|-|7
2.57.122.193|-|7
2.57.219.2|-|7
5.101.0.66|-|7
5.180.253.220|ptr.default|7
23.249.28.102|-|7
36.110.228.254|-|7
71.6.199.23|einstein.census.shodan.io|7
72.194.234.244|wsip-72-194-234-244.ph.ph.cox.net|7
80.82.77.202|rnd.group-ib.com|7
92.118.39.71|-|7
92.118.39.75|-|7
92.255.57.132|-|7
93.126.53.41|-|7
162.142.125.36|-|7
162.142.125.209|scanner-05.ch1.censys-scanner.com|7
162.142.125.217|scanner-05.ch1.censys-scanner.com|7
167.94.145.103|-|7
167.94.145.105|-|7
167.94.145.110|-|7
167.94.146.50|-|7
167.94.146.51|-|7
167.94.146.58|-|7
167.94.146.59|-|7
167.94.146.61|-|7
178.160.211.111|-|7
183.224.219.194|-|7
185.142.236.34|hat.census.shodan.io|7
185.165.191.26|purple.census.shodan.io|7
185.165.191.27|red.census.shodan.io|7
193.32.162.131|-|7
193.32.162.133|-|7
193.32.162.135|-|7
193.32.162.136|-|7
195.178.110.76|-|7
199.45.154.142|scanner-203.hk2.censys-scanner.com|7
206.168.34.38|-|7
207.90.244.2|-|7
218.92.0.111|-|7
218.92.0.114|-|7
218.92.0.198|-|7
218.92.0.216|-|7
218.92.0.217|-|7
218.92.0.218|-|7
218.92.0.220|-|7
218.92.0.221|-|7
218.92.0.222|-|7
218.92.0.223|-|7
218.92.0.225|-|7
218.92.0.226|-|7
218.92.0.227|-|7
218.92.0.228|-|7
218.92.0.229|-|7
218.92.0.230|-|7
218.92.0.232|-|7
218.92.0.233|-|7
218.92.0.235|-|7
218.92.0.236|-|7
218.92.0.237|-|7
103.147.14.129|-|7
103.87.207.254|-|7
135.125.238.48|vps-4a663f72.vps.ovh.net|7
15.235.2.68|ip68.ip-15-235-2.net|7
184.168.122.184|184.122.168.184.host.secureserver.net|7
185.29.121.79|ddos-protect.berkinnet.com|7
208.109.188.104|s2plnebfssn019.prod.sdl2.secureserver.net|7
213.55.85.202|-|7
62.36.40.104|mail1.prevecam.es|7
87.248.226.146|87.248.226.146.pool.sknt.ru|7
89.168.18.25|-|7
