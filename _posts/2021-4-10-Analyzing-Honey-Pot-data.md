### Top Passwords
```
  80795 "admin"
  19147 ""
  16412 "nproc"
  11052 "password"
   5011 "123456"
   2237 "12345"
   2206 "123"
   1202 "1234"
    708 "1"
    556 "root"
```

### Top Usernames
```
  163133 "root"
  16421 "nproc"
   2074 "admin"
   1248 "test"
    837 "user"
    638 "ubuntu"
    623 "postgres"
    481 "oracle"
    432 "ftpuser"
    413 "git"
```
The command used to gather the results is: `cat cowrie.json* | jq '. | select(.username) | .username'  | sort | uniq -c | sort -bgr | head -10`

### Top TCP-IPs
```
  64006 "23.235.255.50"
  59573 "i.instagram.com"
  46773 "ip-who.com"
  39797 "67.205.145.217"
  25264 "www.google.ru"
  23137 "ya.ru"
  22283 "www.google.com"
  21841 "23.52.19.209"
  17731 "2a00:1148:db00::8"
  15890 "23.194.4.99"
```
The command used: `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.direct-tcpip.request")) .dst_ip' | sort | uniq -c | sort -bgr | head -n 10`
### Top FAILED IPs
These are the top 10 IPs that tired to login into the honeypot unsuccessfully.
```
    245 "199.195.248.34"
    203 "51.158.123.160"
    184 "159.65.128.182"
    183 "49.232.161.195"
    183 "134.122.69.50"
    183 "106.13.55.94"
    179 "8.40.143.51"
    179 "106.38.158.131"
    174 "170.106.155.226"
    173 "203.99.62.158"
```
The command used was `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.login.failed")) .src_ip' | sort | uniq -c | sort -bgr | head -n 10`

### Top SUCCESSFUL IPs
These are the top IPs that where successfully able to login into the honeypot.
```
  33761 "47.113.95.46"
  17731 "194.88.107.163"
  11377 "190.2.144.57"
   8345 "45.227.255.163"
   8101 "194.88.107.165"
   7842 "5.188.86.174"
   5942 "45.227.255.205"
   3339 "190.2.144.45"
   3145 "89.39.105.84"
   2538 "5.182.39.62"
```
The command use to get the results: `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.login.success")) .src_ip' | sort | uniq -c | sort -bgr | head -n 10`

### Downloads
```
    16510 "/root/.ssh/authorized_keys"
    113 "/var/tmp/.var03522123"
    110 "/tmp/up.txt"
     36 "/yoyotftp2.sh"
     36 "/yoyotftp1.sh"
     18 "/cp"
      9 "/home/phil/.ssh/authorized_keys"
      4 ""
      2 "/var/tmp/.systemcache436621"
```
The command used was: `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.session.file_download")) | .destfile' |  grep -v "null" | sort | uniq -c | sort -bgr | head -n 10`

### Top Commands
```
  33761 "echo -e \"\\x6F\\x6B\""
  16754 "cat /proc/cpuinfo | grep name | wc -l"
  16704 "cat /proc/cpuinfo | grep name | head -n 1 | awk '{print $4,$5,$6,$7,$8,$9;}'"
  16702 "uname"
  16695 "free -m | grep Mem | awk '{print $2 ,$3, $4, $5, $6, $7}'"
  16686 "which ls"
  16686 "ls -lh $(which ls)"
  16679 "crontab -l"
  16667 "w"
  16657 "uname -m"
```
The command used to gather the results is : `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.command.input")) | .input' | sort | uniq -c | sort -bgr | head -n 10`
