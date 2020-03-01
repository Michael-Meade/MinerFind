# How sign up works
When the user signs up, a randomly generated password is created. During the singup proccess, the scritp will use the <a href="https://github.com/net-ssh/net-ssh">net-ssh gem</a> to login into the player server and create a user. After the information is entered into database and the Linux user is created on the player server, a text file will be downloaded. Inside this text file, includes the players team_name, irn and the randomly generated password.<br><br>

For the player to login to the player server, they need to use the following command: ```ssh team_name@player_server_ip```. The password inside text file that was download is the users password.<br>

# How Scoring works
Every minute, a crontab runs the script ```cron.rb```. Cron.rb will visit the players web sever address ( https://player_ip/index.html ).
If the team name matches a team name in the db then they will be rewared 50 points. It is imporant to note that if the ```/var/www/html``` direcotry has incorrect permissions no one will be able to gain any points. Also if the team name does not a existing record than no points will be rewared. <br>
