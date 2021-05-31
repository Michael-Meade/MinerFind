### Top File Download
```ruby
     183 "http://107.172.249.148/x86_64"
     54 "http://134.122.65.100/yoyobins.sh"
     40 "http://88.218.17.110/bins/Oblivion121.x86"
     36 "tftp://134.122.65.100/yoyotftp2.sh"
     36 "tftp://134.122.65.100/yoyotftp1.sh"
     24 "http://45.14.149.204/x86_64"
     18 "http://71.127.148.69/.x/2sh"
     18 "http://71.127.148.69/.x/1sh"
     12 "http://alavojda.do.am/a.txt"
      9 "http://71.127.148.69/.x/3sh"
```

### Top Failed IP 
These are the IPS of the failed login attempts to the honey pot.
```ruby
    245 "199.195.248.34"
    200 "150.158.176.46"
    184 "159.65.128.182"
    183 "49.232.161.195"
    183 "134.122.69.50"
    183 "106.13.55.94"
    179 "8.40.143.51"
    179 "49.235.33.85"
    179 "106.38.158.131"
    177 "101.33.124.250"
```

### Top Passwords
The top 10 passwords attempted.
```ruby
  52894 "admin"
  19636 "nproc"
  12887 ""
  12010 "password"
   6261 "123456"
   2530 "123"
   2504 "12345"
   1228 "1234"
    841 "1"
    621 "root"
```

### Top Users
The top 10 usernames attempted.
```ruby
  132541 "root"
  19636 "nproc"
   2209 "admin"
   1392 "test"
    823 "user"
    747 "ubuntu"
    718 "postgres"
    576 "oracle"
    532 "ftpuser"
    481 "git"
```

### Top commands
The top 10 commands entered aftery they logged on.

```ruby
  33761 "echo -e \"\\x6F\\x6B\""
  19994 "cat /proc/cpuinfo | grep name | wc -l"
  19950 "uname"
  19948 "cat /proc/cpuinfo | grep name | head -n 1 | awk '{print $4,$5,$6,$7,$8,$9;}'"
  19940 "free -m | grep Mem | awk '{print $2 ,$3, $4, $5, $6, $7}'"
  19932 "which ls"
  19932 "ls -lh $(which ls)"
  19924 "crontab -l"
  19913 "w"
  19903 "uname -m"
```
The command below is the command that was used to get the Top 10 commands.
`cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.command.input")) | .input' | sort | uniq -c | sort -bgr | head -n 10`


### Top Successful Logins
THe top ten Successful logins
```ruby
  33761 "47.113.95.46"
  14804 "194.88.107.163"
   9188 "194.88.107.165"
   5822 "45.227.255.163"
   5445 "5.188.86.174"
   4202 "45.227.255.205"
   2242 "190.2.144.45"
   2174 "89.39.105.84"
   1670 "5.182.39.61"
   1641 "5.182.39.63"
```
The command below is the command that was used to get the Top ten succesful Logins.

`cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.login.success")) .src_ip' | sort | uniq -c | sort -bgr | head -n 10`



### Top TCP IP

These are IPS that are attempting to use the honey pot as a proxy.
```ruby
  54007 "ip-who.com"
  52300 "23.235.255.50"
  49043 "i.instagram.com"
  29920 "67.205.145.217"
  19518 "www.google.ru"
  16513 "ya.ru"
  15778 "rogers-fido.janraincapture.com"
  15644 "23.52.19.209"
  14804 "2a00:1148:db00::8"
  14292 "www.google.com"
```

The command used to get this data from the logs is: cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.direct-tcpip.request")) .dst_ip' | sort | uniq -c | sort -bgr | head -n 10
