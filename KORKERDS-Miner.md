<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
<br>
According to hybrid-analysis.com, there is multiple XMR Linux based malware. One of the XMR Linux based malware is known as 1.sh. Referring to Figure 1, there are multiple scripts that are listed there. The first script has the functionality of killing any processes that might be a competing miner. The second script is the “c” function where it runs: ```chattr -i /usr/local/bin/dns /etc/cron.d/root /etc/cron.d/apache /var/spool/cron/root /var/spool/cron/crontabs/root /etc/ld.so.preload.```
The third script uses curl to download a bash script from ```hxxps://pastebin.com/raw/CnPtQ2tM.``` The script downloads the file into the user’s ```/usr/local/bin/dns``` directory. Refer to Figure 1 for further detail of the scripts. <br>
<img src="https://i.imgur.com/9OUnw47.png =100x20" alt="Octocat" /><br>
Figure 1: Shows the 1.sh script
<br>
<br>
To ensure persistence on the box. The script creates a new cronjob that edits current commands every 10 minutes. There is also an option for the script to be set up in such way that it could update current commands every 13 and 27 minutes. 
According to Figure 2, the pastebin.com link shows the malware adding the cronjob is base64 obfuscated. The deobfuscated script is uploaded to https://pastebin.com/raw/td5KhzVC. The script’s functionality is to determine if the infected machines is x64 or x86 or x32. Depending on the type of arch the machine is, it will download the minor that is compatible with the arch machine to the /tmp/kworkerds directory. The script also includes functions where it edits the command. Refer to Figure 2 for further detail of the script. 
<img src="https://i.imgur.com/6y5wqOs.png =100x20" alt="Octocat" /><b>
  Figure 2: Shows the pastebin.com link<br>
  
  ### Scanner 
  In the 1.sh script, the function of “c” is to decode a base64 string and runs the decoded base64 script. Refer to Figure 3 for a full picture of the script. 
<p><img src="https://i.imgur.com/F4SOGcU.png =100x20" alt="Octocat"/><br>
  Figure 3: Shows the C function<br>
  
  The script in Figure 2 will execute the python script that is hosted on https://pastebin.com/raw/hQZTFAdC. I uploaded the deobfuscated script to https://pastebin.com/raw/yyrk9MZj. The Python script generates IP addresses and checks for any running file servers or an IP camera on TCP port 8161.

### Downloading of the Miner

The creator of the script registered the scripts to a domain called master.minerxmr.ru. This was done privately to ensure the domain to be secure. The bash script undergoes the process of checking the type of Linux machine system. If the Linux machine is x64 or x86, the bash script will download a miner from hxxps://master.minerxmr.ru/1/1551434761x2728329064.jpg. In the scenario that the Linux system is x32 bit, then the bash script will download the miner from hxxps://master.minerxmr.ru/2/1551434778x2728329032.jpg. Both of these versions of the miners are downloaded to the machine’s ```/var/tmp/kworkerds``` directory.
