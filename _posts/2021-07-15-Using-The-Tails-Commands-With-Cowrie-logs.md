### Tails Commmands
A basic example of the tails is shown below. 
```bash
tail -f cowrie.json 
```


### Displaying successful login attempts
The command below will show all the Ips, username and passwords that were used to login into the honey pot. 

```bash
tail -f cowrie.json | jq -r '. | select(.eventid | contains("cowrie.login.success")) | "IP:" +  .src_ip,"Username:" + .username,"Password: " + .password + "\r\nn" '
```

### Displaying information about commands
The command below can be used to view information about commands that are entered on the honeypot. The command will display three pieces of information such as the command entered, the Session ID and the Source IP. 

The Session ID could be used to view other activity that the hacker performed during that session. 

```bash
tail -f cowrie.json | jq -r '. | select(.eventid | contains("cowrie.command.input")) | "CMD: " + .input, "Session: " + .session,  "SRC IP: " + .src_ip + "\r\n"'
```
