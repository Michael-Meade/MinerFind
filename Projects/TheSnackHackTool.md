### The idea behind the name
There are many different types of snacks, they come in all types: crunchy, soft, sugarly, natural. This tool does not have one single purpose.
How it works is that there is a 'plugin' or modular like system that a user could create a module to add a certain functionality to the project. This makes it easy for new features to be added to the tool without having mess with the main part of the code. 

The end user can choose what modular they want to run, or run a bunch of them together. The tool will save the results of the scan 
as reports.  The formats that it currently supports is JSON & TXT files. 


### Senior Project
This tool is also being created for my Senior Projects. My senior Project is to create a standard that could be 
used by web site administrators to limit the amount of inforamtion that could be used by attackers to exploit or attack the 
site. It is stil in the working but it will set up a bunch of guidelines like: 
- Remove the server header in the requests
- Check for SSRF
- Check  & remove any  default pages ( server-info, server-status, etc )
- Makes sure that there is not any sensitive inforamtion that is exposed in the robots.txt file



### Source code
The code for the project can be found <a href="https://github.com/Michael-Meade/snack_hack">here</a>