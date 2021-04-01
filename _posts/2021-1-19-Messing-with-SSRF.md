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

If the vulnerable web app was live on the internet, attackers might also be able to access internal services used on the server. Some companies will create an locally hosted site in their internal networks. This usually is not accessible if to anyone that is not connected to the network. It could allow attackers to access local files, services such as FTP, HTTP, Mysql or any other services.

<img src="https://i.imgur.com/cbMXRXd.png">


### Abusing SSRF for Port checking

Companies that want extra protection from hackers, might not setup a service on a standard port. They might do this to make it harder for the hackers to fingerprint the service. Most HTTP servers like  Apache and ngix have a server-name header in the response of each request made. This can be also be removed to make it harder for the attackers to figure out what HTTP server the server is using. 


Other services like FTP have banners that they might display that will usually tell what FTP server the site is using. 


To show how SSRF can be abused to check ports on the internal server, we have to create a new web app. The new web look like this:

```ruby
require 'sinatra'
set :port, 3333
get '/' do
	puts response.status
end

```

Siantra allows you to use `set :port, 3333` to set the port you want to use. A attacker could use a script like this to scan the internal network of a site. 

```ruby
require 'excon'
s = 3299
for i in s..3399
    puts Excon.get("http://localhost:4567/?url=http://localhost:#{i}").status
end
```
The script will loop through a bunch of nubmers and use the puts method to print out the status of the repsonse. A attcker could use this information to map out the internal network. The attacker could even use different protocols.



### SSRF Scan
<a href="https://github.com/Michael-Meade/SSRF-Scan">SSRF Scan</a> is a basic tool that is able to check for SSRF vulnerabilities. The tool will scan through all the ports through 1 and 65535. If the request comes back with a status 200 code then it will assume that it is vulnerable. This might give false postives if the site responds back with a status 200 code but displays an error on the page. 

### Running the program
```
ruby test.rb --url http://localhost:4567?url=SSRF -ps http://127.0.0.1
```
The SSRF is needed to tell the program what parameter to try to check to see if it is vulnerable. 
