# How sign up works
When the user signs up, a randomly generated password is created. During the singup proccess, the scritp will use the <a href="https://github.com/net-ssh/net-ssh">net-ssh gem</a> to login into the player server and create a user. After the information is entered into database and the Linux user is created on the player server, a text file will be downloaded. Inside this text file, includes the players team_name, irn and the randomly generated password.<br><br>

For the player to login to the player server, they need to use the following command: ```ssh team_name@player_ip```. The password inside text file that was download is the users password.<br>

