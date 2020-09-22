---
title: "Cowrie Log parser"
description: "A tool coded in ruby to parse cowrie log and save the information in json files"
tags: [cowrie log, parser]
---

# About
This is probably my third or so time attempting to code a Cowrie log scraper. But this time is different because I experimented with design patterns. Design pattern's purpose is to make the code more organized. Which makes it easier to fix problems and add more features.


# What I learned
The whole idea of the 'get_links' method was to create an array of all the URLs that were accessed. "h" is the array I created to store all the URLs. Arrays are usually in the following format. ```[ "1". "2", "3". "4", "5" ]```. The value between each of the " " is called an element. I wanted to make sure that there were no duplicates of the same element.


<img src="https://i.imgur.com/cC6BbkJ.png" alt="cowrie" width="400" height="350"><br>
Instead of having the code above which uses Ruby's include? method to check to see if the URL is not one of the elements of the array. The ```include?```  method will return true if the supplied string is an element. If it does not contain the supplied string it will return false. I used the ```!``` operator to tell it if it <b>does not contain</b> the supplied string to do the next step, which is to add the URL to the array. I used the ```<<``` operator which will append it to the array. But doing this way was kinda buggy and chunky. I wanted to improve on it. I was bored one-day coding and was just looking at the code to decide what I should add next. It came to me there that coding is like writing an essay for school.


You have to give it a look over and proof read the code. When coding something I usually have an idea of what it should do and how I should do it. When coding functions that might be complex I like to break down the idea into chunks.  I work on the first chunk.
Once I am satisfied  that chunk works, I will move onto the next chunk. and so on. This also makes it easier to debug becuase you are only focusing on a small part of the code. This allows me to make sure that the idea of functionally is actually possible before putting all the pieces together.  But when I work on each chunk I take short cuts and use bad coding methods.<br>

After I get the whole idea working as a whole is when I start to pretty up the code. Its usually changing up methods, variables names, or simplizing the lines.  Sometimes I will create new folder names in my ruby directory, work on an idea in that directory. Make sure that everything works, after I am happy that everything is working I will implement the idea into the project directory. <br>

<img src="https://i.imgur.com/L3lAL1v.png" width="400" height="350"><br>
After doing some Googling, I found this on <a href="https://stackoverflow.com/questions/14004325/add-element-to-an-array-if-its-not-there-already">stackoverflow.</a>. This cool little feature allows you enter an element into an array. It will check before it enters to make sure the element is unique and there is no repeats. I choose to do this becuase I wanted it to only show all the commands entered into terminal but not show repeats. This can be done by using ```|=``` operator. This will only enter the element into the array if it is unique. 


### The features

## Cowrie::Commands
```Cowrie::Commands.all("cowrie-9-21-2020.json")```<br>
This method will get both all the commands and any links that were found in the Cowrie output. This could be used to download samples from the site.


## Cowrie::SaveCommands
```Cowrie::SaveCommands.get_links("cowrie.json") ```<br>
This method coule be used to get all the URLS that is in the Cowrie output.

```Cowrie::SaveCommands.get_commands("cowrie.json")```<br>
This method will get all the commands that the attackers have entered. This could be used to find out what command is being entered the most. 

## Cowrie::TopTen
```Cowrie::TopTen.success_failed("cowrie.json")```<br>
This method will the amount of times that an attacker has failed to login into the SSH 

```Cowrie::TopTen.success_success("cowrie.json")```<br>
This method does the same as the above but for the successful logins into the SSH.

```Cowrie::TopTen.success_both("cowrie.json")```<br>
This method gets both the success and failed login attempts.

```Cowrie::TopTen.top_ssh("cowrie.json")```<br>
Get the Top Ten SSH hash. This could be used to figure out what amount attemps is the same attacker

```Cowrie::TopTen.daily("cowrie.json", "src_ip", "cowrie.login.success")```<br>
The "cowrie.json" is where the user should enter what ever the name of their log file. The second argument is for what ever the user wants to scrape. In this example, it is grabbing the ```src_ip```. The last argument is for the event id. In this example, the user wanted only get information from attackers that succesfully logged in. But a user could change it to:
- cowrie.login.failed
- cowrie.login.success
- cowrie.direct-tcpip.redirect
- cowrie.client.version
- cowrie.session.closed
- cowrie.command.input
- cowrie.direct-tcpip.request
<br><br>
The top ten daily function will create a file like the following:
``` {"08-17-2020":[{"admin":3176,"1234":8}]} ```
The method what ever date it is that day and create a array of that has the key and the amount of of times the data was entered. 


## Cowrie::Time

```Cowrie::Time.date("9-21-2020-cowrie.json")```
```Cowrie::Time.time("9-21-2020-cowrie.json")```

These will get the days or time and save them to a file. It will save them in the time.json or date.json depending on what method is used.

Example of output is: 

```{"Sunday":44,"Friday":2624,"Saturday":5048,"Monday":4874}```

The class it uses is named ```DateTime```. Orginally I wanted it the class name to be ```Time``` but it gave an error. I think it  was already being used by the
time class. This is a class that is built into Ruby that allows users to do stuff with the date or time. Such as get the current date, format the date in different ways.






