### Looking into the domain

After peaking into the bash script I noticed the following line ```declare -a temp_remote_host=("auth.to0ls.com" "111.90.140.35")```
The site's index page looked like Figure 1. 

![auth.to0ls.com-index-page](https://i.imgur.com/JrDEpmk.png=100x20)<br>
Figure 1, the index page<br>

But after looking at the source code for the index page it becomes clear that its all a clever ruse. Figure 2, shows the source code for the index page.
![auth.to0ls.com-source-code](https://i.imgur.com/9oC60D7.png=100x20)<br>
Figure 2, source code of the index page.<br> 

In figure 2 we can see that a couple of things seems a little off. First off the year is wrong. Secondly who is ```David Colagiovanni``` that is named in the title element?
After doing some digging with Google. I found this site: <a href="http://classic.rhizome.org/artbase/artwork/50465/">http://classic.rhizome.org/artbase/artwork/50465/</a><br><br>
The article is about an artist named ```David Colagiovanni``` who created the site ```http://www.seizethisdoma.in/``` to try to mimic ICE's seizure that they place on seized domains..<br>
My bet is that the author of the Linux rootkit used this site's source code as a ruse to trick researchers into thinking that the domain was seized.<br>

Looking at the whois records for the domain backs up the theory because the domain was created on the date of ```2019-06-04```. Sadly thats about all the inforamtion that the whois records can provide since the <br>
attackers used WHOIS protection. 

## A dive into the malware
![BasicInitFunction](https://i.imgur.com/gMjmXcR.png=100x20)<br>
Figure 3, BasicInit Function<br>

The code in Figure 3, first checks to make sure that it is able to ping the domains ```auth.to0ls.com``` and ```111.90.140.35```. 
The script pings the two domains to check if the domain is up. The script will then create the variable named ```remote_host``` with whatever site is up at the time the script is ran.<br>
The function will run a command to check if the user id is equal to ```0```. If the script is determines that the user is root, then it will give the variable ```shell_privilege``` the value of 0. If it detects that the user id is something other than 0 it will give the variable  ```shell_privilege``` the value of 1. The script will also give the variable ```DownloadPath``` the value of ```/home/$USER/...```.<br>

Next the script will create a new directory with the name of the value of ```DownloadPath```. It also gives the new directory ```777``` permissions. 

The last thing the function does is check to see what operating system the machine is. 



<b>Urls and domains</b><br>
auth.to0ls[.]com<br>
111.90.140[.]35<br>
