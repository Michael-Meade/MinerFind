
### The log file

<img src="https://i.imgur.com/OlKKF60.png" alt="http://209.141.32.204" width="70%" height="35%">
<br>
The command below was used in the screenshot above to scrape & print information about a session in which the user tires to use my honeypot to mine Moner.

```bash
tail -f cowrie.json | jq -r '. | select(.eventid | contains("cowrie.command.input")) | "CMD: " + .input, "Session: " + .session,  "SRC IP: " + .src_ip + "\r\n"'
```
