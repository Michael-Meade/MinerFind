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
```
