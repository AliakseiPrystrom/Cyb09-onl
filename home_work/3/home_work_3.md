## 1. CPU info logging with sort

**listing:**
- ps aux --sort=%cpu >> cpulogfile 2 > /dev/null (дефолтное решение)
- ps aux --sort=-%cpu | head -6 >> cpulogfile 2>/dev/null (использовал это, что бы выводило не всю простыню)

### Correct
![info](home_work/3/img.png)
### With error (wrong syntax)
![info](home_work/3/img_1.png)

## Parallels thread

**listing:**
- ps aux -u user --sort=-%mem | head -11 | tee memlog.log && cat memlog.log

### Result
![info](home_work/3/img_2.png)


### nmap
**listing:**
- nmap --top-ports 1000 -oG - scanme.nmap.org | grep -v "^#"

```
Host: 45.33.32.156 (scanme.nmap.org)    Status: Up
Host: 45.33.32.156 (scanme.nmap.org)    Ports: 22/open/tcp//ssh///, 25/filtered/tcp//smtp///, 26/filtered/tcp//rsftp///, 80/open/tcp//http///, 88/filtered/tcp//kerberos-sec///, 513/filtered/tcp//login///, 646/filtered/tcp//ldp///, 990/filtered/tcp//ftps///, 1433/filtered/tcp//ms-sql-s///, 2001/filtered/tcp//dc///, 2121/filtered/tcp//ccproxy-ftp///, 3986/filtered/tcp//mapper-ws_ethd///, 5666/filtered/tcp//nrpe///, 6646/filtered/tcp/////, 8443/filtered/tcp//https-alt///, 49153/filtered/tcp/////, 49155/filtered/tcp/////, 49156/filtered/tcp///// Ignored State: closed (82)
```

- sudo nmap -sV -O -p 22,80,443,8000-8100 scanme.nmap.org

```
Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-04 12:23 -0400
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.095s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 102 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.7
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: VoIP adapter|bridge|general purpose
Running (JUST GUESSING): AT&T embedded (93%), Oracle Virtualbox (92%), Slirp (92%), QEMU (90%)
OS CPE: cpe:/o:oracle:virtualbox cpe:/a:danny_gasparovski:slirp cpe:/a:qemu:qemu
Aggressive OS guesses: AT&T BGW210 voice gateway (93%), Oracle Virtualbox Slirp NAT bridge (92%), QEMU user mode network gateway (90%)
No exact OS matches for host (test conditions non-ideal).
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 65.39 seconds

```


- nmap -iL targets.txt --top-ports 1000 -T4 -oG quick_scan.txt

```
targets.txt:
 159.65.220.10 176.120.22.47 2.57.122.196 91.202.233.33 2.57.121.118 45.148.10.147 45.227.254.170 2.57.121.17 195.178.110.15 185.156.73.233 217.154.35.203 13.81.183.30 92.118.112.178 168.167.228.123 217.60.39.166 163.7.8.79 51.79.84.112 124.105.173.17 91.92.243.116 61.23.36.232 213.167.43.130 201.184.50.251 2.57.122.192 2.57.122.190 2.57.122.193 139.59.9.151 2.57.122.194 45.148.10.152 43.252.231.122 2.57.122.199 91.224.92.50 45.148.10.141 2.57.122.197 2.57.122.238 2.57.122.195 45.148.10.157 2.57.121.50 2.57.122.189 115.241.83.2 2.57.122.188 2.57.121.69 2.57.121.86 2.57.122.191 45.148.10.151 27.50.25.190 87.251.64.141 92.118.39.56 197.227.8.186 165.154.6.136 104.248.232.41 79.168.139.28 156.245.239.180 41.86.34.139 80.94.92.184 202.165.17.230 92.118.39.95 159.146.11.164 197.5.145.114 103.228.37.49 176.120.22.17 101.47.48.255 171.25.158.58

```

```
Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-03 13:09 -0400
Stats: 0:00:04 elapsed; 0 hosts completed (0 up), 62 undergoing Ping Scan
Parallel DNS resolution of 62 hosts. Timing: About 11.29% done; ETC: 13:09 (0:00:24 remaining)
Stats: 0:00:05 elapsed; 0 hosts completed (0 up), 62 undergoing Ping Scan
Parallel DNS resolution of 62 hosts. Timing: About 12.90% done; ETC: 13:09 (0:00:27 remaining)
Stats: 0:00:07 elapsed; 0 hosts completed (0 up), 62 undergoing Ping Scan
Parallel DNS resolution of 62 hosts. Timing: About 20.97% done; ETC: 13:09 (0:00:23 remaining)
Warning: 2.57.121.69 giving up on port because retransmission cap hit (6).
Warning: 176.120.22.17 giving up on port because retransmission cap hit (6).
Warning: 45.148.10.151 giving up on port because retransmission cap hit (6).
Warning: 45.148.10.152 giving up on port because retransmission cap hit (6).
Warning: 2.57.121.86 giving up on port because retransmission cap hit (6).
Warning: 176.120.22.47 giving up on port because retransmission cap hit (6).
Warning: 195.178.110.15 giving up on port because retransmission cap hit (6).
Warning: 45.227.254.170 giving up on port because retransmission cap hit (6).
Warning: 197.5.145.114 giving up on port because retransmission cap hit (6).
Warning: 45.148.10.147 giving up on port because retransmission cap hit (6).
Warning: 91.92.243.116 giving up on port because retransmission cap hit (6).
Warning: 2.57.122.238 giving up on port because retransmission cap hit (6).
Warning: 168.167.228.123 giving up on port because retransmission cap hit (6).
Warning: 41.86.34.139 giving up on port because retransmission cap hit (6).
Warning: 165.154.6.136 giving up on port because retransmission cap hit (6).
Warning: 103.228.37.49 giving up on port because retransmission cap hit (6).
Warning: 124.105.173.17 giving up on port because retransmission cap hit (6).
Warning: 217.60.39.166 giving up on port because retransmission cap hit (6).
Warning: 27.50.25.190 giving up on port because retransmission cap hit (6).
Warning: 2.57.122.192 giving up on port because retransmission cap hit (6).
Warning: 2.57.122.197 giving up on port because retransmission cap hit (6).
Warning: 91.224.92.50 giving up on port because retransmission cap hit (6).
Warning: 2.57.121.17 giving up on port because retransmission cap hit (6).
Warning: 2.57.122.195 giving up on port because retransmission cap hit (6).
Warning: 92.118.39.56 giving up on port because retransmission cap hit (6).
Warning: 87.251.64.141 giving up on port because retransmission cap hit (6).
Warning: 80.94.92.184 giving up on port because retransmission cap hit (6).
Warning: 2.57.121.118 giving up on port because retransmission cap hit (6).
Warning: 2.57.122.196 giving up on port because retransmission cap hit (6).
Warning: 115.241.83.2 giving up on port because retransmission cap hit (6).
Warning: 91.202.233.33 giving up on port because retransmission cap hit (6).
RTTVAR has grown to over 2.3 seconds, decreasing to 2.0
Stats: 0:11:06 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 22.78% done; ETC: 13:56 (0:36:16 remaining)
Stats: 0:31:51 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 47.01% done; ETC: 14:16 (0:35:27 remaining)
Stats: 1:40:00 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 95.12% done; ETC: 14:54 (0:05:06 remaining)
Stats: 2:01:26 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 98.81% done; ETC: 15:12 (0:01:28 remaining)
Stats: 2:08:35 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.69% done; ETC: 15:18 (0:00:24 remaining)
Stats: 2:08:57 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.70% done; ETC: 15:18 (0:00:23 remaining)
Stats: 2:11:52 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.78% done; ETC: 15:21 (0:00:18 remaining)
Stats: 2:18:23 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.90% done; ETC: 15:27 (0:00:08 remaining)
Stats: 2:18:24 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.91% done; ETC: 15:27 (0:00:08 remaining)
Stats: 2:18:28 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.91% done; ETC: 15:27 (0:00:08 remaining)
Stats: 2:19:55 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.93% done; ETC: 15:29 (0:00:05 remaining)
Stats: 2:20:25 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.95% done; ETC: 15:29 (0:00:05 remaining)
Stats: 2:20:37 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.95% done; ETC: 15:29 (0:00:04 remaining)
Stats: 2:20:47 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.95% done; ETC: 15:29 (0:00:04 remaining)
Stats: 2:21:03 elapsed; 0 hosts completed (62 up), 62 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 99.96% done; ETC: 15:30 (0:00:04 remaining)
Nmap scan report for 159.65.220.10
Host is up (0.13s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
8080/tcp closed http-proxy
9878/tcp closed kca-service

Nmap scan report for 176.120.22.47
Host is up (0.067s latency).
Not shown: 988 closed tcp ports (reset)
PORT      STATE    SERVICE
22/tcp    open     ssh
25/tcp    filtered smtp
311/tcp   filtered asip-webadmin
1050/tcp  filtered java-or-OTGfileshare
3001/tcp  filtered nessus
3986/tcp  filtered mapper-ws_ethd
5811/tcp  filtered unknown
5825/tcp  filtered unknown
8031/tcp  filtered unknown
8080/tcp  open     http-proxy
49157/tcp filtered unknown
57294/tcp filtered unknown

Nmap scan report for 2.57.122.196
Host is up (0.20s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE    SERVICE
25/tcp   filtered smtp
5679/tcp open     activesync
8099/tcp filtered unknown

Nmap scan report for 91.202.233.33
Host is up (0.060s latency).
Not shown: 921 filtered tcp ports (no-response), 77 closed tcp ports (reset)
PORT     STATE SERVICE
22/tcp   open  ssh
8080/tcp open  http-proxy

Nmap scan report for dns118.personaliseplus.com (2.57.121.118)
Host is up (0.075s latency).
Not shown: 998 closed tcp ports (reset)
PORT     STATE    SERVICE
25/tcp   filtered smtp
5679/tcp open     activesync

Nmap scan report for 45.148.10.147
Host is up (0.050s latency).
Not shown: 926 filtered tcp ports (no-response), 73 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for 45.227.254.170
Host is up (0.052s latency).
Not shown: 920 filtered tcp ports (no-response), 79 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for hosting17.tronicsat.com (2.57.121.17)
Host is up (0.19s latency).
Not shown: 998 closed tcp ports (reset)
PORT     STATE    SERVICE
25/tcp   filtered smtp
5679/tcp open     activesync

Nmap scan report for 195.178.110.15
Host is up (0.049s latency).
Not shown: 942 filtered tcp ports (no-response), 57 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for 185.156.73.233
Host is up (0.0049s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
111/tcp  open   rpcbind
2323/tcp closed 3d-nfsd
3128/tcp open   squid-http
3390/tcp closed dsc
5222/tcp closed xmpp-client
9878/tcp closed kca-service

Nmap scan report for ip217.154.35-203.pbiaas.com (217.154.35.203)
Host is up (0.0069s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
9878/tcp closed kca-service

Nmap scan report for 13.81.183.30
Host is up (0.0077s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
256/tcp  open   fw1-secureremote
443/tcp  open   https
9878/tcp closed kca-service

Nmap scan report for 152165.ip-ptr.tech (92.118.112.178)
Host is up (0.0061s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
443/tcp  open   https
9878/tcp closed kca-service

Nmap scan report for 168.167.228.123
Host is up (0.0051s latency).
Not shown: 973 filtered tcp ports (no-response), 26 closed tcp ports (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 217.60.39.166
Host is up (0.12s latency).
Not shown: 995 closed tcp ports (reset)
PORT      STATE    SERVICE
19/tcp    filtered chargen
22/tcp    open     ssh
25/tcp    filtered smtp
6002/tcp  filtered X11:2
34572/tcp filtered unknown

Nmap scan report for 163.7.8.79
Host is up (0.22s latency).
Not shown: 994 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   closed http
443/tcp  closed https
3389/tcp closed ms-wbt-server
5222/tcp closed xmpp-client
9878/tcp closed kca-service

Nmap scan report for vps-08a8fb7b.vps.ovh.ca (51.79.84.112)
Host is up (0.0063s latency).
Not shown: 998 filtered tcp ports (no-response), 1 filtered tcp ports (net-unreach)
PORT     STATE  SERVICE
9878/tcp closed kca-service

Nmap scan report for 124.105.173.17
Host is up (0.0056s latency).
Not shown: 914 filtered tcp ports (no-response), 81 closed tcp ports (reset)
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
3306/tcp open  mysql
8007/tcp open  ajp12

Nmap scan report for 91.92.243.116
Host is up (0.065s latency).
Not shown: 951 closed tcp ports (reset), 48 filtered tcp ports (no-response)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 61-23-36-232.rev.home.ne.jp (61.23.36.232)
Host is up (0.0066s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT     STATE  SERVICE
9878/tcp closed kca-service

Nmap scan report for mx3.volgaltd.ru (213.167.43.130)
Host is up (0.0059s latency).
Not shown: 992 filtered tcp ports (no-response)
PORT     STATE  SERVICE
53/tcp   open   domain
80/tcp   open   http
443/tcp  open   https
1022/tcp open   exp2
2000/tcp open   cisco-sccp
8080/tcp open   http-proxy
8291/tcp open   winbox
9878/tcp closed kca-service

Nmap scan report for static-adsl201-184-50-251.une.net.co (201.184.50.251)
Host is up (0.0067s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
443/tcp  closed https
9878/tcp closed kca-service

Nmap scan report for 2.57.122.192
Host is up (0.041s latency).
Not shown: 906 filtered tcp ports (no-response), 93 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for 2.57.122.190
Host is up (0.066s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT     STATE  SERVICE
1067/tcp closed instl_boots
3325/tcp closed active-net
5679/tcp open   activesync
9878/tcp closed kca-service

Nmap scan report for 2.57.122.193
Host is up (0.0056s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
1199/tcp closed dmidi
5679/tcp open   activesync

Nmap scan report for 139.59.9.151
Host is up (0.0067s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT     STATE  SERVICE
9878/tcp closed kca-service

Nmap scan report for 2.57.122.194
Host is up (0.0059s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT     STATE  SERVICE
4004/tcp closed pxc-roid
5679/tcp open   activesync
7402/tcp closed rtps-dd-mt
9878/tcp closed kca-service

Nmap scan report for 45.148.10.152
Host is up (0.050s latency).
Not shown: 937 filtered tcp ports (no-response), 62 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for 43.252.231.122
Host is up (5.6s latency).
Not shown: 989 filtered tcp ports (no-response)
PORT     STATE  SERVICE
20/tcp   closed ftp-data
21/tcp   closed ftp
22/tcp   open   ssh
80/tcp   open   http
443/tcp  closed https
801/tcp  closed device
888/tcp  open   accessbuilder
1027/tcp closed IIS
6007/tcp closed X11:7
7103/tcp closed unknown
8888/tcp closed sun-answerbook

Nmap scan report for 2.57.122.199
Host is up (0.058s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT     STATE  SERVICE
4998/tcp closed maybe-veritas
5679/tcp open   activesync
9485/tcp closed unknown
9878/tcp closed kca-service

Nmap scan report for imize2.writeresaychooseboltsnow.com (91.224.92.50)
Host is up (0.062s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE    SERVICE
25/tcp   filtered smtp
5679/tcp open     activesync
8089/tcp filtered unknown

Nmap scan report for 45.148.10.141
Host is up (0.0063s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
5679/tcp open   activesync
9878/tcp closed kca-service

Nmap scan report for 2.57.122.197
Host is up (0.16s latency).
Not shown: 998 closed tcp ports (reset)
PORT     STATE    SERVICE
25/tcp   filtered smtp
5679/tcp open     activesync

Nmap scan report for 2.57.122.238
Host is up (0.048s latency).
Not shown: 852 filtered tcp ports (no-response), 146 closed tcp ports (reset)
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Nmap scan report for 2.57.122.195
Host is up (0.18s latency).
Not shown: 998 closed tcp ports (reset)
PORT     STATE    SERVICE
25/tcp   filtered smtp
5679/tcp open     activesync

Nmap scan report for 45.148.10.157
Host is up (0.0070s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
5679/tcp open   activesync
9878/tcp closed kca-service

Nmap scan report for smtp50.kcmoa.com (2.57.121.50)
Host is up (0.059s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
5679/tcp open   activesync
9878/tcp closed kca-service

Nmap scan report for 2.57.122.189
Host is up (0.0066s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT      STATE  SERVICE
5679/tcp  open   activesync
9878/tcp  closed kca-service
10000/tcp closed snet-sensor-mgmt

Nmap scan report for 115.241.83.2
Host is up (0.0040s latency).
Not shown: 754 closed tcp ports (reset), 244 filtered tcp ports (no-response)
PORT     STATE SERVICE
22/tcp   open  ssh
3128/tcp open  squid-http

Nmap scan report for 2.57.122.188
Host is up (0.0071s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
5679/tcp open   activesync
9878/tcp closed kca-service

Nmap scan report for mta69.soniideas.com (2.57.121.69)
Host is up (0.052s latency).
Not shown: 725 filtered tcp ports (no-response), 274 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for mta86.soniideas.com (2.57.121.86)
Host is up (0.046s latency).
Not shown: 939 filtered tcp ports (no-response), 60 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for 2.57.122.191
Host is up (0.041s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT      STATE  SERVICE
648/tcp   closed rrp
5679/tcp  open   activesync
9878/tcp  closed kca-service
32783/tcp closed unknown

Nmap scan report for 45.148.10.151
Host is up (0.050s latency).
Not shown: 936 filtered tcp ports (no-response), 63 closed tcp ports (reset)
PORT     STATE SERVICE
5679/tcp open  activesync

Nmap scan report for ip-27-50-25-190.cepat.net.id (27.50.25.190)
Host is up (0.0059s latency).
Not shown: 969 filtered tcp ports (no-response), 29 closed tcp ports (reset)
PORT    STATE SERVICE
22/tcp  open  ssh
443/tcp open  https

Nmap scan report for 87.251.64.141
Host is up (0.16s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE    SERVICE
22/tcp open     ssh
25/tcp filtered smtp

Nmap scan report for 92.118.39.56
Host is up (0.21s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE    SERVICE
22/tcp open     ssh
25/tcp filtered smtp

Nmap scan report for 197.227.8.186
Host is up (0.0072s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
9878/tcp closed kca-service

Nmap scan report for 165.154.6.136
Host is up (0.19s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE    SERVICE
22/tcp open     ssh
25/tcp filtered smtp

Nmap scan report for 104.248.232.41
Host is up (2.6s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
5222/tcp closed xmpp-client
9878/tcp closed kca-service

Nmap scan report for a79-168-139-28.cpe.netcabo.pt (79.168.139.28)
Host is up (0.13s latency).
Not shown: 992 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
3000/tcp open   ppp
3389/tcp open   ms-wbt-server
4000/tcp open   remoteanything
9000/tcp open   cslistener
9003/tcp open   unknown
9009/tcp open   pichat
9878/tcp closed kca-service

Nmap scan report for 156.245.239.180
Host is up (0.0055s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
9878/tcp closed kca-service

Nmap scan report for 41.86.34.139
Host is up (0.18s latency).
Not shown: 997 closed tcp ports (reset)
PORT   STATE    SERVICE
22/tcp open     ssh
25/tcp filtered smtp
80/tcp open     http

Nmap scan report for 80.94.92.184
Host is up (0.20s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE    SERVICE
22/tcp open     ssh
25/tcp filtered smtp

Nmap scan report for 202.165.17.230
Host is up (0.0068s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT     STATE  SERVICE
9878/tcp closed kca-service

Nmap scan report for 92.118.39.95
Host is up (0.0057s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE  SERVICE
22/tcp   open   ssh
9878/tcp closed kca-service

Nmap scan report for 159.146.11.164
Host is up (0.0069s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT     STATE  SERVICE
3030/tcp open   arepa-cas
3389/tcp open   ms-wbt-server
9878/tcp closed kca-service

Nmap scan report for 197.5.145.114
Host is up (0.073s latency).
Not shown: 926 closed tcp ports (reset), 73 filtered tcp ports (no-response)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 103.228.37.49
Host is up (0.0072s latency).
Not shown: 954 filtered tcp ports (no-response), 44 closed tcp ports (reset)
PORT     STATE SERVICE
22/tcp   open  ssh
3306/tcp open  mysql

Nmap scan report for 176.120.22.17
Host is up (0.083s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE    SERVICE
22/tcp   open     ssh
25/tcp   filtered smtp
8080/tcp open     http-proxy

Nmap scan report for 101.47.48.255
Host is up (0.0057s latency).
All 1000 scanned ports on 101.47.48.255 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap scan report for 171.25.158.58
Host is up (0.0061s latency).
Not shown: 994 filtered tcp ports (no-response), 1 filtered tcp ports (net-unreach)
PORT     STATE  SERVICE
22/tcp   open   ssh
8080/tcp open   http-proxy
8383/tcp open   m2mservices
8800/tcp open   sunwebadmin
9878/tcp closed kca-service

Nmap done: 62 IP addresses (62 hosts up) scanned in 8616.36 seconds
```
Analytics:
```
1. Порт 5679 (ActiveSync) открыт на 25+ хостах (2.57.122.x, 45.148.10.x) - возможны RCE уязвимости Exchange (ProxyLogon/ProxyShell)
2. Хост 213.167.43.130 имеет порт 8291 (Winbox MikroTik) - известные RCE уязвимости (CVE-2018-14847, CVE-2023-30799)
3. Хост 124.105.173.17 критичен: открыты SSH, DNS, HTTP, MySQL (3306) и AJP12 (8007) - уязвимость Ghostcat позволяет читать файлы
4. Хост 79.168.139.28 открыт RDP (3389) + нестандартные порты 3000,4000,9000,9003,9009 - возможен брутфорс RDP
5. Сети 2.57.122.0/24 и 45.148.10.0/24 содержат множество однотипных хостов с activesync - вероятно единая инфраструктура хостинга
```







