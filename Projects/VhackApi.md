## VhackOs Api
VhackOS is hacking sim game for android. 

## Looking at requests
![Octocat](https://i.imgur.com/B4DH0sA.png=100x20)
Looking at the ```user``` param we can see that the information is base64 encoded. When I decoded the string it looked like the following.
<br>
```ruby
{"password":"5f4dcc3b5aa765d61d8327deb882cf99","lang":"en","username":"chickenWings"}
```
The hash included the md5 password, the language that they signed up with and the Username. The server responds to the login request by sending all the authenciated users game stats. The inforamtion that is included is the user's accessToken and the user's UID. 
![OCtocat](https://i.imgur.com/PlUlePj.png=100x20)<br>

The ```login(username, password``` module first takes the password variable and creates a Md5 hash. Next the using the variable name of ```login_info``` the code creates a hash with the username, password and user language. 
<br>
![OCtocat](https://i.imgur.com/s2d2n1u.png=100x20)
