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
