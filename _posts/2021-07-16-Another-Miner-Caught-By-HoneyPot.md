
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
The image below shows the contents of `http://209.141.32[.]204/.ssh`. Right of away, two files grab my attention. The `config.json` and the `krane` file. These grab my attention because those files were created just three days ago.<br><br>
<img src="https://i.imgur.com/SGZIAVk.png" alt="http://209.141.32[.]204/.ssh" width="35%" height="35%">

## Config.json
The `config.json` file also caught my eye because config.json files are often used by miners for mining. 
The following Monero address was being used for the mining. The pool that was being used was "hashvault.pro".

`49ubSTdDp9hPmYE7paRM6PZFLmqvsedZ56MXLUT8mvYnTzjVCKGDbpuW4RVdvZon228uWnkjoJN8S6w5S4LdgeK8UBMMEhJ`

Most miners have a feature built into the miner that allows the user to donate some of their hashes to the developers. This miner might donate all their hashes to the developers 1 minute every hour. The value was set as 1, this is intresting becauase they author of the malware was donating their hash power to the developers.  This might be on purpose or a careless mistake of a inexperienced malware author. 

### The .db directory
<img src="https://i.imgur.com/DI2TCio.png" alt="http://209.141.32[.]204/.db" width="35%" height="35%">
<br>
The image above shows the contents of the .db directory. The directory contains a handful of text files that are used by the malware to brute force machines that have SSH exposed.<br>

<img src="https://i.imgur.com/DFAvqKD.png" alt="http://209.141.32[.]204/.db" width="35%" height="35%"><br>
The image above shows the contents of pass.txt. The pass.txt file contains popular passswords and usernames. 

### IOC
dfa6d202fc24623a5aadf3684aadcfbce72ee8aa  config.json<br>
f1cb326ee8ab4217cf9191f395e35fe684dd426a  a<br>
bfa1d6ecc6a4f2da893b88f15b96a96320dd27c5  b<br>
d987680671c4c35610d659dd5dc2e0f4d387e0b4  pass.txt<br>
3fbbd4ef15e064bd2f4b8b643aacbafdfc347833  dump.txt<br>
16e358574ef61f841f8b6ddb45188446c7da8c7d  k<br>
