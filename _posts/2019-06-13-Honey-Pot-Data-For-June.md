---
layout: post
title:  "Analyzing Honey Pot data"
---
We are going to look through the honey pot data from ```6-4-2019 - 6-13-2019```. I set up a simple honeypot using [Cowrie](https://github.com/cowrie/cowrie). Setting up the honey pot was pretty easy.  I choose this honey pot becuase it had a large following and a bunch of features. Instead of using the suggested output organizer, I have been exporting the logs to my pc every morning and then using ruby scripts I wrote to parse the data.

## Attempted Logins Stats

In Figure 1 we can see that there was a staggering 44k logins with the username ```ruby root```. Which makes sense because a attacker would want root access to the machine so they could bascily do anything they want with the machine. 
![Top to usernames](https://i.imgur.com/hFOtHSN.png=100x20)<br>
Figure 1, Top 10 Username logins

In Figure 1, there was 44,014 logins for root but in Figure 2, there was 44,030 password logins using ```admin```. All the passwords used are common passwords that would be found in a password list. With the expection of password ```usuario```. After some Googling I found out that it is spanish for ```ruby user```. 
![Top 10 Passwords](https://i.imgur.com/M6kF6cG.png=100x20)<br>
Figure 2. Top 10 Password logins


