# Purpose
The purpose of the alert system is to make it easier for person running the event to fix problems. Alert's goal is to make it so that all
the errors are rescued and sent in a speical dicord channel. Hopefully this will make it easier for the admin to figure out issues and fix them.


# Discord bot
The alert system uses discord as default but anything could be used. 
The user can add their Discord token, channel id and client in the discord.json file.
To find the channel_id all the user needs to do is visit the channel in a web browser and go to the channel that they want to use. Just copy the last number in 
the URL and add it to the json file. Now the admin should go to their devoplers dashboard and copy their token. This is needed to use the bot. 
Do not share this token because anyone with access to it will be able to read/send messages on the behalf of the bot. 

# What does it do?
Below is an example of what the message will look like.
![Octocat](https://i.imgur.com/tT2d7xK.png=100x20)<br>
If the user wants to add something to the alert system, all they would have to do is create an rescue statement and put this in the end.
```ruby
begin
  Blah.blah
rescue => e
   Alerts.check_status(e, "cron.rb")
end
```
E is should be where the error actually error is displayed and where "cron.rb" is should be the file name and method that it is rescuing. It is imporant to 
put what file and method it is rescuing becauase it will make it easier to trouble shoot the problem.
