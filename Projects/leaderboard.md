---
layout: post
title: How the Blue vs Blue scoreboard works.
tags: blue-vs-blue, scoreboard, king of the hill, linux, sqlite3, ruby
---
# How sign up works
When the user signs up, a randomly generated password is generated. During the singup proccess, the script will use the <a href="https://github.com/net-ssh/net-ssh">net-ssh gem</a> to login into the player server and create a user on the system.  
While that is being done, the scoreboard server inserts the new user's information into the database.
After the information is entered into database and the Linux user is created on the player server, a text file will be downloaded in the new users browser. Inside this text file, includes the players team_name, irn and the randomly generated password.<br><br>

For the player to login to the player server, they need to use the following command: ```ssh team_name@player_server_ip```. After running the command, the user should be prompted for a password. The password for their account is in the text file that was downloaded.

# How Scoring works
Every minute, a crontab runs the script ```cron.rb```. Cron.rb will visit the players web sever address ( https://player_ip/index.html ). In this case "index.html" would be considered the **scoring_file**
If the contents of the ```scoring_file``` matches a user in the scoreboard's users database, than the script will increase their score by 50 points. 

It is imporant to note that if the ```/var/www/html``` direcotry has incorrect permissions, no one will be able to gain any points. Also if the team name does not match any users in the database. Then no points will be rewarded. <br>

# Recommendation
It is Recommended to have the scoreboard server and the player server on different boxes. This is recommended for a couple different reasons. 
One reason is because it is safer for the integrity of the game. It will limit the risks of players messing with the scoring server or trying to change the score in the database. Another reason is so that if someone accidently does something or something happens and people are unable to access the server you don't have to worry about the scoring server becuase it is not effected by that mistake.

Another recommendation is to use 
<a href="https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server">key authenciation</a> for the scoring server. If the server is facing the internet, it will be scanned by people that will try to brute force their way in. Using key auth to sign in will make it impossible for them to compromise the server.<br>
Orginally I wanted the players to login using key auth, for a couple of different reasons. 

One being that it would make it impossible for the account to be compromise. Another reason was to give the player the out of the class room experience  of using keys to login to SSH. But I decided against this because it would make it harder on the player and might discourage users from playing. 
