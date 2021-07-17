
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

### K 
The 'k' file can be found at `http://209.141.32[.]204/k`. In order to ungzip the file, we need to use the `cp k k.gz` commmand to add the 
gz extension to the file. This is needed so we can ungzip the file. Next we used `gzip -d k.gz` to ungzip the file. The result ended with a new file named 'k.tar`. Once again we have to use the command `cp k k.tar` to change the file's extension to .tar. Lastly we use the command 
`tar -xvf k.tar` to untar the file. The results are a new hidden folder named `.k`. 

```
a:             ASCII text
boner:         ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, for GNU/Linux 2.6.24, stripped
k_config.json: JSON data
main:          ELF 64-bit LSB shared object, x86-64, version 1 (GNU/Linux), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=6585c7cd03ec265663087a7edaa517813514e9fa, for GNU/Linux 3.2.0, not stripped
ra:            ASCII text
rx:            ASCII text
send_vuln.py:  Python script, ASCII text executable
ta:            ASCII text
tx:            ASCII text
x:             ASCII text
```
The snippet above shows the contents of the .k.tar directory. 


### IOC
dfa6d202fc24623a5aadf3684aadcfbce72ee8aa  config.json<br>
f1cb326ee8ab4217cf9191f395e35fe684dd426a  a<br>
bfa1d6ecc6a4f2da893b88f15b96a96320dd27c5  b<br>
d987680671c4c35610d659dd5dc2e0f4d387e0b4  pass.txt<br>
3fbbd4ef15e064bd2f4b8b643aacbafdfc347833  dump.txt<br>
16e358574ef61f841f8b6ddb45188446c7da8c7d  k<br>
ad4649a79b67c1db9a8343e18af3b7c0d323172c  a
a9c7d059a22fed787f48698c5c10b0b5146f616d  boner
9c9a96383883601d9ad8a7d78eb3995a7dfbc350  k_config.json
2ccf0c37b004b1793dd79792dc6ffd83e7438137  main
1f8f3d751b578242e9c2b32391c8a162e154c7b2  ra
e5dcaab24fab63b050a5a80b50f5a9ad17d127f1  rx
638108b2217b21843ba7f1c80a95f756e5e2310d  send_vuln.py
a82a8eda9177b2ef1e8936784d0aa5d79fa2ddce  ta
e85c6b190d672884a4a37039cb35dfc73a84318a  tx
f5f323005f8c71324c53c864d28db4cbed8e78ac  x<br>
