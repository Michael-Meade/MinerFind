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

```
The command used: `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.direct-tcpip.request")) .dst_ip' | sort | uniq -c | sort -bgr | head -n 10`

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
