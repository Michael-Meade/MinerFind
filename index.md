---
layout: default
---
## Script Information
I was searching through hybrid-analysis.com and I stumbled on to a bash script that looked like its used for deploying mining scripts on Linux machines. From looking at the file, it looks like that it's job is to download a couple of other scripts that will download a bunch of other scripts.<br>
<br>

![Octocat](https://i.imgur.com/pvtH2iu.png =100x20)

From what I understand from Bash, the script creates a function called ```Check()``` that will download the other files. Check() has two argurments, I labled the arguments <b><font color="red">1</font></b> and <b><font color="blue">2</font></b>.
<br>
<br>
The first argument <font color="red"><b>1,</b></font> is the url where the scritp is hosted. The second argument <font color="blue"><b>2,</b></font> is the where it will download the script on the victim's machine. 
<br><br>
The first file that the scripts downloads is: ```http://132.148.148.79/plus/kok```. The downloaded script will check and remvoe any other competing miners. The script checks if there are any matching strings in the cronjob and uses the grep command to check for anyother strings in the proccess. It wil then kill the processes. 
<br>
<br>
The second url in the first script will download a script from ```http://132.148.148.79/plus/wow```. This script once ran will download a file from ```https://pastebin.com/raw/zwJ7M9et```. The script that is hosted on pastebin is base64 obfuscated. 
THe deobfuscated script looks like this: <br>

![Octocat](https://i.imgur.com/esGa2VS.png =100x20)
<br>
<br>

The last script that the orginal script download is the actual payload. The orginal script downloads the last script from ```http://132.148.148.79/plus/rc7```
![Octocat](https://i.imgur.com/JaHI09x.png=100x20)
<br><br>
I installed the script on my subsystem so it might be a little different than a pure Linux box. 
But the last script downloads all the payloads to the ```/tmp/.dbb/``` directory. 
## Pool and Address Info
The Attackers are using the open source miner  ```xmr-stak```.  
Looks Like they are using the MineXmr.com as the pool and the link we found might be a proxy. Both malicious and legit miners use  proxy so they don't overload the pool with traffic and it allows legit miners to better mangage their hash rate. Malicious miners like to use it because it decreases the chances of them getting banned from the pool because to the pool it looks like only one worker is made instead of huge amound of workers. 
<br><br>
Using shodan we can see that the mining proxy is located in Singapore and are using OVH as the hosting. 

![Octocat](https://i.imgur.com/2ee97aq.png =100x20)
At the time of the writing the actors have made $110.33. They also have only $4.90 in pending. 
<br>
![Octocat](https://i.imgur.com/4N9h0iu.png =100x20)
From the data available on minexmr, they started to mine on Jan 3 2019.
The website ```https://www.xmrhunter.com/``` is a handy site that scrapes a bunch of xmr pools and returns how much a certain address has made on that site. According to the xmrhunter the person or people behind this mining campaign also used the mining pool, dwarfpool. They only made $0.02 on this pool and was last seen January 14, 2019. They were never paid for the $0.02. 


## ICO
<b>IPs || Sites</b><br>
      <p>
            hxxp://132.148.148.79<br>
            hxxp://pastebin.com/raw/zwJ7M9et<br>
            hxxp://minexmr.com<br>
            hxxp://139.99.120.75:443<br>
            hxxp://139.224.20.173<br>
      </p>
<b>XMR address</b><br>
      <p>
            4Ak4rRJHzo4SsxQWRcMGJpBRKCokRVRGc5v599tJhQBSczmvXRBAmWETEDX8xYhwUhAVZCCupHULDJFPNrmb9AErLtZfEaK<br>
      </p>
<b>Hashes</b><br>
      <p>
            SHA1 e09e9b2d8fbd25b8129c0577eeba82d3eb783415 2e2c93911f787a72422d41d7c8858a073e081a4181e27091fff558dc9ed3f7be.sh
            SHA1 ebf60b6e4ca6a3d7c59b4f950d58196a69412b05 kok
            SHA1 1eb6978d0e463248ad36f6ce8da7b13b488e5260 nx.2.sh
            SHA1 8ffc58caa11dd7efedf0d4fb655231a99a10cf20 wow
            SHA1 59e96f96ecd1af0745eb705a4545bf0eb3f69028 zwJ7M9et
            SHA1 82433c8374a954a7daa7fbdb9e35e346dbd78bd3 nx 
            SHA1 dcfbdb2fe2f0d29c213e23b6b10e9da813bae9d3 rc7
      </P>
<b>AV</b><br>
      <p>
            hxxps://www.hybrid-analysis.com/sample/2e2c93911f787a72422d41d7c8858a073e081a4181e27091fff558dc9ed3f7be
      </p>
