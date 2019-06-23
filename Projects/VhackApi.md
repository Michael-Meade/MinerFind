## VhackOs Api
VhackOS is hacking sim game for android. 

## Looking at requests
![Octocat](https://i.imgur.com/B4DH0sA.png=100x20)
Looking at the ```user``` param we can see that the information is base64 encoded. When I decoded the string it looked like the following.
<br>
```ruby
{"password":"5f4dcc3b5aa765d61d8327deb882cf99","lang":"en","username":"chickenWings"}
```
We can see when decoding the base64 that it includes the md5 hash of the password, as well as the language and the Username.


The server responds to the login request by sending all the authenciated users game stats. The inforamtion that is included is the user's accessToken and the user's UID and their game stats.
![OCtocat](https://i.imgur.com/PlUlePj.png=100x20)<br>
## Creating the code to login.
The ```login(username, password)``` module first takes the password variable and creates a Md5 hash. With the ```hashed_info``` we take a the ```login_info``` and create a MD5 hash with it as well as convert the varaible ```login_info``` into a josn string.<br>

Next we take the ```hashed_info``` variable and then create a MD5 hash with it. This is will become the ```pass``` param when we log in.<br>

Next we create the ```user``` parm by taking  ```login_info``` and base64 encoding it for the user param.

![OCtocat](https://i.imgur.com/AbLVy2n.png=100x20)
<br>
Next we convert the vaiable ```login_info```  into a json string. We are just adding to the json key & value.
