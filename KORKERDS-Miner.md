<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
<br>
Once again, I found this sample on hybrid-analysis.com. The file named was ```1.sh```. 
## Killing The Competition
Like pretty much any other XMR linux based malware, the first thing this malware does is kill any processes that might be a competing miner. <br>
![Octocat](https://i.imgur.com/9OUnw47.png =100x20) Figure A
<br>
Next the script runs the c function. The first thing the c function does is run this command. <br>
```chattr -i /usr/local/bin/dns /etc/cron.d/root /etc/cron.d/apache /var/spool/cron/root /var/spool/cron/crontabs/root /etc/ld.so.preload```
Next the script uses curl to download a bash script from ```hxxps://pastebin.com/raw/CnPtQ2tM```. The script downloads the file into the user's ```/usr/local/bin/dns``` directory. <br>
<br>
To insure that the malware stays on the machine if the owner removes it. The script creates a new cron job. The new cron job edits the cron job every 10 minutes. But it also edits it every 13 & 27 minutes. <br>
![Octocat](https://i.imgur.com/6y5wqOs.png =100x20) Figure B, The hxxps://pastebin.com/raw/CnPtQ2tM script<br>

The pastebin.com link that the malware adds to the cron job is base64 obfuscated. I uploaded the deobfuscated script to ```https://pastebin.com/raw/td5KhzVC```

The script job is to determine if the infected machine is x64 or x86 or x32. Depending on what arch the machine is it will download the miner to the ```/tmp/kworkerds``` directory.  The script also includes functions where it edits the cron again.


## Scanner

In the original script ( 1.sh ) function c decodes a base64 string and then runs the decoded base64 script. As seen in the figure, C.

![Octocat](https://i.imgur.com/F4SOGcU.png =100x20) <br>Figure C<br>
The deobfuscated python script in figure C, looks like this. The script in figure B will execute the python script that hosted at ```https://pastebin.com/raw/hQZTFAdC```. This script is also base64 obfuscated. I uploaded the deobfuscated script to ```https://pastebin.com/raw/yyrk9MZj```.
The Python script generates a bunch of IP's and then checks to see if they are running a file server or an IP camera on TCP port 8161.


## Downloading of the Miner
The creator of the script registered the domain ```master.minerxmr.ru```. Which of course the creator used privacy setting when creating the domain.<br>
First, the bash script checks if its the Linux machine is x64 or x86. If it is x64 or x86 the script then download the miner from ```hxxps://master.minerxmr.ru/1/1551434761x2728329064.jpg```
<br>
If the script detects otherwise than it downloads the x32 bit miner from ```https://master.minerxmr.ru/2/1551434778x2728329032.jpg```
Both versions of the miner download to the machines ```/var/tmp/kworkerds``` directory.
