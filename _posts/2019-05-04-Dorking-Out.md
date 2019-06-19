<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
---
layout: post
title:  "Dorking Out"
---


## Dorking out
Dorks is a tool that can be used to find vulnerable devices, sites that contains sensitive information, or malware samples online. 
<br>
## Getting Alerts
Google has a function that allows users to get alerts through the URL “https://www.google.com/alerts”. Google will first “crawl” the site before an alert is made. In this project, the creation of a Gmail account must be done to experiment for the use of Google’s Alert system. It is set up in such a way that it will send alerts to the Gmail account. Refer to Figure 1 as to how a Gmail account would look like when a Google Alert system is set up. <br>
![Octocat](https://i.imgur.com/1BIxuMG.png=100x20)<br>
                                 Figure 1: Shows the Gmail account that contains the Google alerts

<br>
In addition, a project that could be done with the use of Google Alert is to search for other researcher’s reports on malware. Sites such as Pastebin.com, github.com, and gist.github.com may contain potential malware samples. This will help end users to be safe on the internet and also help individuals to obtain reports that a specific website may contain malware.
<br>
## Hybrid 
Google contains operators that help end users to find specific information online. In regards to Dorking Out, a specific search is used in Figure 2 that had an outcome of 370 results in the Google search. When using the quotation operator “ ” in Google, it specifies the end result to only return results that match the entire string. In the case of finding malware samples, the command to use is “grep -v grep overview login to download”. The outcome of the Google search is 24 which indicates that it is most likely be malware samples. <br>
![Octocat](https://i.imgur.com/nYbFSup.png=100x20)<br>
                                    Figure 2: shows the "" operator in Google Search
<br>

## Finding Samples on Pulbic Sites
For example, Xbash Malware can be found on Pastebin.com and Github.com through using dorks via the search:<br>
```("rootv2.sh" | "r88.sh" | "lowerv2.sh") ``` <br>
```filetype: sh ("rootv2.sh" | "r88.sh" | "lowerv2.sh") ``` <br>

This command will find files on the internet with the same file names as the attackers use on websites such as Pastebin.com and Github.com. In the command above, the operator <b>|</b> is used as the <b>OR</b> operator where it searches a bunch of strings that are specific to the search. Also, the site: operator is used as a parameter for Google in order to specify a limitation in the result of the search. Refer to Figure 3 as to how the search operators are used to find a specific email from pastebin.com <br>

![Octocat](https://i.imgur.com/sN30kiv.png=100x20)<br>
Figure 3: Shows the Site: and the " " operator used to find a specific email address in a Google Search.
