
### The log file

<img src="https://i.imgur.com/OlKKF60.png" alt="http://209.141.32.204" width="70%" height="35%">
<br>
The command below was used in the screenshot above to scrape & print information about a session in which the user tires to use my honeypot to mine Moner.

```bash
tail -f cowrie.json | jq -r '. | select(.eventid | contains("cowrie.command.input")) | "CMD: " + .input, "Session: " + .session,  "SRC IP: " + .src_ip + "\r\n"'
```
The image below shows the results of the DirSearch scan of 209.141.32[.]204. The image shows that the IP has a couple of hidden directories and a handful of other files. 
<img src="https://i.imgur.com/TGUCk5q.png" alt="http://209.141.32.204 dirsearch" width="35%" height="35%">

### The hidden .ssh directory
The image below shows the contents of `http://209.141.32[.]204/.ssh`. Right of away, two files grab my attention. The `config.json` and the `krane` file. These grab my attention because those files were created just three days ago. 
<img src="https://i.imgur.com/SGZIAVk.png" alt="http://209.141.32[.]204/.ssh" width="35%" height="35%">

## Config.json
The `config.json` file also caught my eye because config.json files are often used by miners for mining. 
The following Monero address was being used for the mining. The pool that was being used was "hashvault.pro".

`49ubSTdDp9hPmYE7paRM6PZFLmqvsedZ56MXLUT8mvYnTzjVCKGDbpuW4RVdvZon228uWnkjoJN8S6w5S4LdgeK8UBMMEhJ`



### IOC
dfa6d202fc24623a5aadf3684aadcfbce72ee8aa  config.json<br>
f1cb326ee8ab4217cf9191f395e35fe684dd426a  a<br>
bfa1d6ecc6a4f2da893b88f15b96a96320dd27c5  b<br>
