## About

<a href="https://github.com/Michael-Meade/Leaderboard">leaderboard</a> is a updated version of <a href="https://github.com/Michael-Meade/blue-vs-blue">blue-vs-blue</a>.<br>
It's basicly the same thing but with a few improvments. Instead of using just one user for all the players.<br>

When the player signs up using ```localhost:4567``` the script will use <a href="https://github.com/net-ssh/net-ssh">net-ssh</a> to
ssh into the ```player's  box```.  Once connected to the player's box it will use the information sumbitted at sign up along with the randomly generated password that was created using the gem <a href="https://github.com/akinrt/random_password">random_password</a> to create a sudo user on the ```ruby player's box```. I choose for each team to create their own users for a couple different reasons. <br>
One reason is that it allows the operators to ban users that are breaking the rules. Also it allows the players to gain experience with SSH and SSH keys outside of a class room environment. In the future I might add a feature in the future that would allow users to use keys to login. It is important to that the players use randomly generated passwords. This is done to protect it the box from attackers. <br>
After the user signs up, sinatra will download a text file. Inside the text file will be the players randomly generated password,team name, irn. It is important for the players to keep the file scoreboard does not save the file.<br>


After the player creates their account and download their file with the password, they will need to login. <br>
Ubuntu players could use the following command to SSH into the player's box. <br>
```ruby ssh teamm_name@players_ip```
