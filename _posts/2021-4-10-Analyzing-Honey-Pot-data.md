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

### Top IPs
```
```

### Top Commands
```
```
The command used to gather the results is : `cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.command.input")) | .input' | sort | uniq -c | sort -bgr | head -n 10`
