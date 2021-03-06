### URLS 
These are URLS that were used to download malware.
```
     102 "http://107.172.249.148/x86_64"
     18 "http://109.104.151.108/mtro/mbot.x86"
     12 "http://71.127.148.69/.x/2sh"
     12 "http://71.127.148.69/.x/1sh"
      6 "http://71.127.148.69/.x/3sh"
```

### Top passwords
The Top passwords that attackers used to gain access to the honey pot. 
```
   42196 "admin"
   7897 ""
   3606 "password"
    693 "nproc"
    295 "pgj-heu05HQM=bMvz"
    240 "123"
    231 "1234"
    192 "alpine"
    150 "123456"
     67 "12345"
```
The last I wrote a post like this was on  <a href="https://michael-meade.github.io/2021/01/11/Cowrie-Logs.html">11 Jan 2021</a>. Looks like the password "" stole second place from "password". Also on Jan 11th 2020 the 3rd password ranked was "WWG1WGA", which now has disappeared from the list. 

### Top Usernames
The Top ten users names that were used to access the machine
```
    55372 "root"
    693 "nproc"
    272 "admin"
    175 "user"
    152 "test"
     74 "ubuntu"
     67 "user1"
     60 "profile1"
     60 "MikroTik"
     60 "default"
```


### TCP IP
Attckers often try to use hacked machines as proxies to scan sites or even try to brute force them. These are the
top sites that those type of attackers has visited.

```
  45203 "23.235.255.50"
  24512 "67.205.145.217"
  22919 "i.instagram.com"
  16207 "ip-who.com"
  14640 "www.google.ru"
  13478 "www.google.com"
  11451 "ya.ru"
  10492 "23.52.19.209"
   9828 "176.103.56.236"
   8159 "176.103.56.151"
```
### Commands used
These are the top ten commands that were used after logging on to the machine. 
```
    711 "uname -a"
    703 "cat /proc/cpuinfo | grep name | wc -l"
    698 "cat /proc/cpuinfo | grep name | head -n 1 | awk '{print $4,$5,$6,$7,$8,$9;}'"
    697 "free -m | grep Mem | awk '{print $2 ,$3, $4, $5, $6, $7}'"
    696 "which ls"
    696 "ls -lh $(which ls)"
    696 "crontab -l"
    695 "w"
    695 "uname -m"
    693 "uname"
```
These were basically all the same commands that the attackers used when we last did a post like this. The attackers used some of these commands to check to see if it was a honey pot. But they also used some of the commands to see if it is worth dropping a miner on the machine. 

### Top SUCCESSFUL IPS
These are the top ten IPS that the attackers used to successfully login into the machine. 
```
   11377 "190.2.144.57"
   4399 "194.88.107.163"
   4297 "45.227.255.163"
   3950 "5.188.86.174"
   3043 "45.227.255.205"
   1837 "190.2.144.45"
   1612 "89.39.105.84"
   1576 "109.236.89.61"
   1440 "5.182.39.62"
   1434 "62.112.11.8"
```
### Top FAILED IPS
These are the top IPS that attempted to login but they were denied.
```
    245 "199.195.248.34"
    203 "51.158.123.160"
    120 "177.38.33.170"
    120 "171.224.180.125"
    113 "77.245.105.165"
    105 "77.237.73.190"
     96 "180.241.44.109"
     57 "81.161.63.251"
     44 "199.195.251.205"
     37 "109.104.151.108"
```


### The top 10 downloaded file
This list the top ten files that were downloaded by the attackers.
```
     681 "/root/.ssh/authorized_keys"
     13 "/var/tmp/.var03522123"
     12 "/tmp/up.txt"
      2 ""
      1 "/var/tmp/.systemcache436621"
```
It makes sense that the top file was a "/root/.ssh/authorized_keys". This file is used by attackers so they can 
maintain access to the machine. 


### Malicious Files Hash
- https://www.virustotal.com/gui/file/f94d30030d2de8e1d51c6c0fb2f325abed19e4faa4144036102f3d36ab3d6269/detection 
- https://www.virustotal.com/gui/file/ff6f81930943c96a37d7741cd547ad90295a9bd63b6194b2a834a1d32bc8f85d/detection
- https://www.virustotal.com/gui/file/60d6733c1940b62f13cfe42d34c0c43aa73f3b8822d8c21cad5d3ebd6b9f94e2/detection
- https://www.virustotal.com/gui/file/585377407888c0c67400c98c7f82f778fe0a6de7aee7b2d4c8c455e4cf669118/detection
- https://www.virustotal.com/gui/file/7c8b1ee9c8b72aae908c4275bc425b7520c84630da89483ae4f38c977ac4d5e7/detection
- https://www.virustotal.com/gui/file/8fc4e21ce648b1f8be81f87f4e763d83dffe48635563a74a332ae05fa8e87c4b/detection
- https://www.virustotal.com/gui/file/e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855/detection
- https://www.virustotal.com/gui/file/e4fafd804c7c9cf29326d4203a74333b211799798cb49d87adb45b9c52938bec/detection
- https://www.virustotal.com/gui/file/1fa16aa1aaebe7a28ce893329d06d34b243ecafd34afd4c8d0a17aa4cc3f3563/detection
- https://www.virustotal.com/gui/file/a8460f446be540410004b1a8db4083773fa46f7fe76fa84219c93daa1669f8f2/detection
- https://www.virustotal.com/gui/file/535bec00a71b8e721a29274c0ccbd88a8d3c43a7f6072730b20e6c21d24fd6bb/detection
- https://www.virustotal.com/gui/file/17c7d210942fda92f998834a01608c1e7154c2caaa4a5cb1a9121a130ca96352/detection

some of the file that are text are not even detected as malicious. While others are detected by VirusTotal. 
