I wanted to learn more about SSRF, so I did some Googling. I eventually found <a href="https://www.hackerone.com/blog-How-To-Server-Side-Request-Forgery-SSRF">this.</a>

I was luckily to find an example of a vulnerable SSRF app that was written in Ruby. 

The vulnerable app is written in <a href="http://sinatrarb.com/">Sinatra</a>. The code used in the example looked liked this:

```ruby
require 'sinatra'
require 'open-uri'
get '/' do
  format  open(params[:url]).read
end
```

To test the URL for SSRF, we would go to this URL in your browser:
```
http://localhost:4567/?url=http://sinatrarb.com/
```

This works becuase the ```open(params[:url]).read``` method is actually going to the inputed URL and sending back it's response. 
This is dangerous because it could also allow attackers to access files or services that are hosted on that server. 



For example, if the server has a config file that is some where in the directory and the attackers are able to guess the name of the file, they might be able to read
or access senstive information such as API keys or passwords. 

I created a hidden file named .config.json file in the same directory as the sinatra script. When I visited the following URL in the browser I was able to read the contents 
of the config file. 

```
http://localhost:4567/?url=.config.json
```


The response was like this:

<img src="https://i.imgur.com/isJRCF8.png">

The attacker would have been able to access the API keys for the application. 



<
