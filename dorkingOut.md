<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
## Dorking out
Dorks can be used to find vulnerable devices or sites with sensitive information. They can be also used for finding malware samples. 
<br>
## Getting Alerts
We could use https://www.google.com/alerts to get alerts if one of search queries shows up on google. Please note that Google first has to crawl the site before an alert is made.<br>
I created a google account that all I use it for is for Google Alerts. If I am standing in line at pio ( the college's 'restaurant' ) or if I am bored I log on into the emails and read the alerts that Google sends it. The accounts inbox looks like this: 
![Octocat](https://i.imgur.com/1BIxuMG.png=100x20)<br>

A researcher could use Google Alert to get alerts about other researcher’s reports about malware. A lot of attackers are using sites like Pastebin.com, github.com, gist.github.com. Which Google likes to crawl those. So Google Alerts can come in handy to get samples. 
<br>
## Hybrid 
![Octocat](https://i.imgur.com/nYbFSup.png=100x20)<br>
In the example above we can see that there are about ```387``` results. That's a pretty good amount. <br>
Using the ```""``` in the search makes Google only return results that matches the entire string. If we wanted the search to only give us results that had malware samples we could add ```Overview Login to Download``` to the query. This gives us, 24 results that will most likely have samples available. 
<br>

## Finding Samples on Pulbic Sites
Google dorks can allow researchers to find scripts or malware that the attackers upload to public sharing sites like pastebin.com and gist.github.com. The Xbash Malware uses Pastebin and GitHub to host some of their files. If we wanted to look for files on the internet with the same filenames as the attackers use we could use the following dorks. <br>
```("rootv2.sh" | "r88.sh" | "lowerv2.sh") ``` <br>
```filetype: sh ("rootv2.sh" | "r88.sh" | "lowerv2.sh") ``` <br>
In the example above ```|``` is used as the ```OR``` operator. The OR operator is used to search a bunch of strings. That search result will give us each all results thats contain those strings.<br>
Using the ```site:``` parameter we limit the results to  only give us results from github.com.<br> 
For an example we could search pastebin.com for a email that is found in the sample. <br>
![Octocat](https://i.imgur.com/sN30kiv.png=100x20)<br>
