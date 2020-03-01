# The Scoreboard Server

The purpose of the scoreboard server is to handle the creation of user accounts, display the leaderboard and rewards players points.

## Files
- cron.rb 
  - Scrapes the playing server's index.html file and if the team name exists it will reward them 50 points. Ran by the cronjob every minute.
- rakefile.rb
  - Makes it easy to creatation of the User table.
  
