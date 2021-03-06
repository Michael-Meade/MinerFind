### Why you might want to limit the information given to the attackers?
By default, Apache2 will include a Server header in every request that includes the version and the name of the web server server that is being used.
A web Site admin might want to limit information like this becuase the information could lead to the website
being attacked if the version has a vulnerability. Especially if the version has a public exploit floating around on the web. 

### Removing the Server Header content from Apache2
This tutorial assumes that you already have Apache2 installed. Now open up the following file in your favorite editor.
`/etc/apache2/conf-enabled/security.conf`

Now look for the line that contains `ServerTokens OS` to `ServerTokens Prod`. Also change the line that contains 
the text `ServerSignature On` to `ServerSignature Off`

Now we have to use the following command to restart the Apache2 service.
```
sudo service apache2 restart
```

Next we have to install libapache2-mod-security2, enter the following command to install the package.
```
sudo apt-get install libapache2-mod-security2
```
modsecurity is a open source firewall that will protect the server from common web vulnerabilities. 
Now that Mod2 is installed, we have to enable firewall by entering the command below. 
```
sudo a2enmod security2
```

Apache2 has to restarted again for the firewall to be deployed. 

Next open up `/etc/apache2/apache.conf` with your favorite text editor. If the text below is not in the file, add the text to the file. If the text is already in the file, change it to match the text below. 


```
<IfModule security2_module>
    SecRuleEngine on
    ServerTokens Min
    SecServerSignature " "
</IfModule> 
```
If you wanted to change the server name to something else, add the text between the two qoutes. 
Now restart the Apache2 service again.

### Checking to see if it worked
Open up a web browser and enter the following URL, "http://localhost:80". 
Now right click on the page and open up a inspect element and click the networking tab. You might need to refresh the page to see any requests. Now click on the request and look at the header information for the request. It should look like something like the image below. 

![no-server-header](https://i.imgur.com/NdrKKrc.png=100x20)<br>

cURL coul also be used to check to see if the server name has been remove. 
Run the following command in a terminal, `curl --head http://localhost`
The output of the command should look similar to the Figure below.



![curl](https://i.imgur.com/413YWes.png=100x20)<br>
