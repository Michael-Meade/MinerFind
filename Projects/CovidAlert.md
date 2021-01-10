#### Background

This is basicly the same idea as <a href="https://michael-meade.github.io/Projects/DiscordMailAlerts.html">this</a>. It will use Google's Atom feed, to scrape my 
EDU. The script is ran by the systems crontab. It wil check my emails every minute for an email that has the header of ```POSITIVE COVID-19 ALERT```. Like the 
mail script it will save the email's publish date to a file. This is done to make sure that the script does not send an alert twice for the same email. 

The code source code can be found <a href="https://github.com/Michael-Meade/GmailCovidAlert">here</a>



### How to get set up
1. Go to https://mail.google.com/mail/u/1/feed/atom. If you have multiple gmails, increase `1` in the URL untill you find the email you want to use.
2. Right click and click inspect
3. Click the network tab. 
4. Refresh the page and select the request with the name atom.
5. Right click and select copy, then select copy all as cURL (bash). Remove the other random requesta but the first one. 
6. Copy the whole curl command into line 35. 
7. Edit your crontab and paste the following command:`* * * * * /bin/bash -l -c 'cd /root/crons/; ruby utica.rb' 
8. Dont forget to change the `/root/crons` with the location of where the sript is, also change `utica.rb` to the name of your script. 
