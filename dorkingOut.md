<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
## Dorking out
Dorks can not be used to find vulnerable devices or sites with senstive information. They can be also used finding malware samples. 
<br>
## Getting Alerts
We could use https://www.google.com/alerts to get alerts if one of search querys shows up on google. Please note that Google first has to crawl the site before an alert is made.<br> I created a google account that all I use it for is for Google Alerts. If I am standing in line at pio ( the college's 'restaurant' ) or bored I log on into the emails and read the alerts that Google sends it. The accounts inbox looks like this: 
![Octocat](https://i.imgur.com/1BIxuMG.png=100x20)
A researcher could use Google Alert to get alerts of other researcher's reports about malware. A lot of attackers are using sites like Pastebin.com, github.com, gist.github.com. So Google Alerts can come in handy to get samples. 
<br>
## Hybrid 
![Octocat](https://i.imgur.com/nYbFSup.png=100x20)<br>
In the example above we can see that there is ```about 387``` results. Thats a pretty good amount. <br>
In the search we used the search parameter <br> ```Site:hybrid-analysis.com``` <br> to only search narrow down the results with that domain.<br> Using the ```""``` in the search makes Google only return results that match the string instead exactly. 
If we wanted the search to only give us results that had malware samples we could add ``` "Overview Login to Download"``` to the query. This gives us, 24 results that mostly likley have a sample.
<br>

## Finding Samples on Pulbic Sites

Google dorks can allow researchers to find scripts or malware that the attackers upload to public sharing sites like pastebin.com and gist.github.com. 
The Xbash Malware that scans the internet looking for vulnerable devices uses pastebin and github to host their files. If we wanted to look for files on the internet with the same filenames as the attackers use we could use the following dorks.
```("rootv2.sh" | "r88.sh" | "lowerv2.sh")``` <br>
```filetype: sh ("rootv2.sh" | "r88.sh" | "lowerv2.sh")```<br>
