<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
<br>

## The main goal
I created this blue vs blue project for <a href="https://www.uccyber.org/">UC3</a>. Its main goal was to help students gain experience with linux outside of class and get members ready for the CNY hackathon.


## What Blue vs Blue?
Before members started, they had to create an Team name. The team name is how they score. To gain points for their team, they had to have their team in a certain file
in the ```/var/www/html``` folder. At first I had set up the scoring server to run a script via a crontab every ten minutes. But I later changed it to every minute. The script that the crontab would run 
would scrape the playing VPS and if the team name matched to a user they would gain 10 points. <b>NOTE: if a player added anything extra in file ( space, extra textt, etc) they would not gain the points.



## Setting it up

When setting up the scoring server, the user needs to install a few gems.
```ruby
gem install mysql2
gem install sinatra
```
<a href="http://sinatrarb.com/">Sintra</a> is a DSL that makes it a breeze to set up web pages.


## Setting it up

The script that is ran by the crontab is named ```cron.rb```. Make sure you change the url in the script to the player VPS IP. 
To get a web server running on the player VPS, first you got to install apache2. Apache2 can be installed by running the following command:
```ruby
sudo apt-get install apache2
```
After apache2 is installed make a file in the ```/var/www/html``` folder. This file can be named anything you want.  But make sure to change the url and the file name
inside ```cron.rb```. 

Next you will need to create a crontab. Crontabs are used to schedule tasks or script. I used the following crontab.
```ruby
*/1 * * * * /bin/bash -l -c 'cd /root/BlueVsBlue/test && ruby crontab.rb'
```
You will probally need to change the file location. To find the file location of where the scripts are use the ```pwd``` command.

