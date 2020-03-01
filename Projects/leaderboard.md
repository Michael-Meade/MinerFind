# The Scoreboard Server

The purpose of the scoreboard server is to handle the creation of user accounts, display the leaderboard and rewards players points.

## Files
- cron.rb 
  - Scrapes the playing server's index.html file and if the team name exists it will reward them 50 points. Ran by the cronjob every minute.
- rakefile.rb
  - Makes it easy to creatation of the User table.
  - run ```rake users```
  - Installs the needed gems
  - run ```rake install```
- config.json
  - the config file. This holds the api key and also the settings
  

## Setting up everything
Running ```rake install``` will install all the needed gems and download slqite. It assumes that the user does not have sqlite installed.<br>


