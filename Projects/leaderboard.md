# How sign up works
When the user signs up, a randomly generated password is created. During the singup proccess, the scritp will use the <a href="https://github.com/net-ssh/net-ssh">net-ssh gem</a> to login into the player server and create a user. After the information is entered into database and the Linux user is created on the player server, a text file will be downloaded. Inside this text file, includes the players team_name, irn and the randomly generated password.<br><br>

For the player to login to the player server, they need to use the following command: ```ssh team_name@player_server_ip```. The password inside text file that was download is the users password.<br>

# How Scoring works
Every minute, a crontab runs the script ```cron.rb```. Cron.rb will visit the players web sever address ( https://player_ip/index.html ).
If the team name matches a team name in the db then they will be rewared 50 points. It is imporant to note that if the ```/var/www/html``` direcotry has incorrect permissions no one will be able to gain any points. Also if the team name does not a existing record than no points will be rewared. <br>

# Recommendation
It is Recommended to have the scoreboard server and the player server on different boxes. This is recommended for a couple different reasons. One reason is because it is safer for the integrity of the game. It will limit the risks of players messing with the scoring server or trying to change the score in the database. Another reason is so that if someone accidently does something or something happens and people are unable to access the server you don't have to worry about the scoring server becuase it is not effected by that mistake.

Another recommendation is to use 
<a href="https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server">key authenciation</a> for the scoring server. If the server is facing the internet, it will be scanned by people that will try to brute force their way in. Using key auth will make it impossible for them to compromise the server.<br>
Orginally I wanted the players to login using key auth, for a couple of different reasons. One being that it would make it impossible for the account to be compromise. Another reason was to give the player the out of the class room experience  of using keys to login to SSH. But I decided against this because it would make it harder on the player and might discourage users from playing. 
