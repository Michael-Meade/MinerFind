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
