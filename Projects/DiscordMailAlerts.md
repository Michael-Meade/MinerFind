### Orgin
When I receive a package, I just need to put my name and the School's address on it. After it comes, I get an email that tells me that I have a package. 
I am not the best at always checking my Email, so I created a system that is able to detect when I have mail and send a message in Discord. Most of the time, I have a Discord tab open in my browser. 


### How it works?
<a href="https://developers.google.com/gmail/gmail_inbox_feed"> Google </a> has a feature that allows you to see your mail as a RSS feed.  To get that feed you have to be currently logged in to Gmail. 

Next you vistit this URL: ```https://mail.google.com/mail/feed/atom```
If you are logged in, then you should see your emails. Now that we are able to get the mail, we have to find the emails that tell me that I have mail. 


The ```GmailAlert``` class looks like this:

```ruby
require 'rss'
require 'open3'
require 'fileutils'
require 'discordrb'
require 'feedjira'
class GmailAlert
    Bot = Discordrb::Commands::CommandBot.new token: '', client_id:  , prefix: '.'
    def discord(title)
      Bot.channel(674737776092250133).send_embed do |embed|
        embed.title = "You Got Mail"
        embed.colour = 0xc033e6
        embed.url = "https://discordapp.com"
        embed.description = "<@315264930951462913> Go pick it up."
        embed.thumbnail = Discordrb::Webhooks::EmbedThumbnail.new(url: "https://i.imgur.com/LdqoGOa.png")
      end
    end
    def get_gmail
      command = %q{URL}
      stdout, status = Open3.capture2(command)
      return stdout
    end
    def run
      FileUtils.mkdir_p 'configs'
      FileUtils.touch(File.join("configs", "tracking.txt"))
      feed = Feedjira.parse(get_gmail)
      feed.entries.each do |line|
        if line.title.to_s.match("You have a package!")
          if !File.read(File.join("configs", "tracking.txt")).to_s.include?(line.published.to_s)
            discord(line.title)
            File.open(File.join("configs","tracking.txt"), "a") { |file| file.write( line.published.to_s + "\n") }
          end
        end
      end
    end
end

GmailAlert.new.run
```
For it to work, you have to go to the Atom page, right click, and then click the networking tab. Copy the request as a cURL command. This is needed so we get the web mail. 

The cURL command goes in the ```get_gamil``` method where the string URL is. 



The ```run``` method, will create a directory named ```configs```. It will also create a file named: ```tracking.txt``` if it does not exist. It will use Feedjira to parse the XML, loop through each line of the XML file. It use Ruby's match method to check to see if the email header contains, the text: ```You have a package!```.
Next it will read the ```tracking.txt``` file and checks if it ```does not``` include the publish date. This is done so it does not keep sending an alert for the same email.After that it will, send the alert using the Discord Ruby gem,. After it does that it will write the publishing date to the ```tracking.txt``` file.


```GmailAlert.new.run``` will run all that .



### Edit the crontab file


To make sure that it will check all the time, we used crontabs.
The command I used is the following: ```* * * * * /bin/bash -l -c 'cd /root/crons/;  ruby package.rb'```. This crontab will the ```package.rb``` file every minute. 



