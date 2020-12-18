### Purpose
The purpose of this rake file is to make it easy to analyze Cowrie honey pot logs. 
The script has a few different features. It can get the top ten, export all the commands, view all the commands. 
The script will read all the JSON Files in that directory.  The rakefile runs bash command with ruby 


# How to use

### Top
Gets the Top Ten Successful IP
```
rake top:sip
```

Get the Top Ten Failed IP
```
rake top:fip
```

Get the Top Ten Passwords
```
rake top:pass
```

Get Top Ten Users
```
rake top:user
```

Top Ten Commands
```
rake top:commands
```

Top TCP IP
```
 rake top:tcpip
```
### Commands

Export commands. This will export all the commands into a file named: out_commands.txt
```
rake commands:export
```

### Download


All the download files
```
rake download:all
```

Top Ten Downloads
```
rake download:top
```

Top Ten URLS
```
rake download:urls
```


Get All the URLS
```
rake download:allurls
```



### Password

Get all passwords
```
rake pass:all
```


Export pass to out_pass.txt
```
rake pass:export
```

### Username

Get all Users
```
rake user:all
```

Export all the users to out_user
```
rake user:export
```
