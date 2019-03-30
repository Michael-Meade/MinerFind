## VhackOs Api
VhackOS is hacking sim game for android. 

## Looking at requests
![Octocat](https://i.imgur.com/B4DH0sA.png=100x20)
The user parameter ```eyJwYXNzd29yZCI6IjVmNGRjYzNiNWFhNzY1ZDYxZDgzMjdkZWI4ODJjZjk5IiwibGFuZyI6ImVuIiwidXNlcm5hbWUiOiJjaGlja2VuV2luZ3MifQ``` is a hash that is base64ed. The decoded base64 string looks like the following.
<br>
```ruby
{"password":"5f4dcc3b5aa765d61d8327deb882cf99","lang":"en","username":"chickenWings"}
```
The hash included the md5 password, the language that they signed up with and the Username. The server responds to the login request by sending all the authenciated users game stats. The inforamtion that is included is the user's accessToken and the user's UID. 
![OCtocat(https://i.imgur.com/PlUlePj.png=100x20)<br>

The  ```login(username, password)``` module is used to login in
![OCtocat(https://i.imgur.com/s2d2n1u.png=100x20)
