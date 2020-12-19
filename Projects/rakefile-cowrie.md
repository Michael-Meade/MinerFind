# About
I have tired to do the same task a couple of times but this one is the one I am most proud of. The other attempts got too complex and had a lot of moving parts. I wanted to do the same thing in simple way. So I thought I would use a rakefile. This makes it easy becauase rakefiles have namespaces where I could organize each of the commands. 
Before I even starting adding code to the rakefile, I tired out the commands in my terminal. After a lot of messing around and Googling I finally was able to have some commands that could do stuff. Next I needed mess to around with the same command I first created but this time I had to modify it so that it fits what I wanted to do. Like save all the UNIQ lines to a text file, get top ten, etc. Next I wrote the acutally rakefile. This was a long proccess because I had to decide how to categorize them in a way that is organized and is consistent. This is something what I really sturggle with so it took a few versions to get something what I think makes sense.


# Purpose
The purpose of this rake file is to make it easy to analyze Cowrie honey pot logs. 
The script has a few different features. It can get the top ten, export all the commands, view all the commands. 
The script will read all the JSON Files in that directory.  The rakefile runs bash command with ruby 

You can find the code at: <a href="https://github.com/Michael-Meade/cowrie-rakefile">here</a>  


# Notes

The rakefile uses similar commands from <a href="https://michael-meade.github.io/2020/11/03/Cowrie-Commands.html">here</a>
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
