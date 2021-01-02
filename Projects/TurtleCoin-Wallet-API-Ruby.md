### TurtleCoin
<a href="https://turtlecoin.lol/">TurtleCoin</a> is a privacy focused coin that was created on February 3,2018. 
Unlike Bitcoin, the blockchain is private, meaning no one that does not have the view key is able to see the transcations. On October 20th, 
<a href="https://blog.turtlecoin.lol/archives/trtl-v2/">TurtleCoin</a> announced that they are planning to relaunch with version2 of TurtleCoin. 
This project is a wrapper for  <a href="https://turtlecoin.github.io/wallet-api-docs/">wallet-api</a>. It's goal is to make it easy to use the TurtleCoin's api wallet.




### How it works?
Before coding the actually wrapper I had to set up and install the Wallet API. I did this on my VPS. I made the the IP accessible on the internet.
In order to connect to the Wallet API, the wrapper will need the following:
- IP
- daemonHost
- daemonPort
- filename
- password
- X-API-KEY

All this information is stored in a JSON file, located at `data/config.json`. Each time the wrapper is ran, it will read from the config file and then connect to the Wallet API. 
The code block below shows that when the HTTP class is called it will Inherit the `ReadConfig` class which basicly just reads the config file and parse it so that we can define the 
information so we can connect to the wallet.
```ruby
class HTTP < ReadConfig
    def initialize
        @ip    = ReadConfig.new.config["ip"]
        @dHost = ReadConfig.new.config["daemonHost"]
        @dPort = ReadConfig.new.config["daemonPort"]
        @fn    = ReadConfig.new.config["filename"]
        @pass  = ReadConfig.new.config["password"]
        @key   = ReadConfig.new.config["X-API-KEY"]
    end
end
```


### Post method

In order to use the Wallet API, the wrapper has to send POST requests to the VPS thats hosting the Wallet API. 
Below is the wrapper's post method. If the `j` is empty it will give the variable a nil value. IF j is not nil then it will use 'j' as the body. 
This is done because some of the Wallet methods require authentication to use and some does. If `j` is nil then it will read from the config file
and put that information in the body of the request. 
```ruby
def post(meth, j = nil)
        if !j.nil?
             l = Excon.post(File.join(ip,meth), :body => j,  :headers => {
            'accept'       => "application/json",
            'X-API-KEY'    => key,
            'Content-Type' => 'application/json',
        })
        puts l.body
        else
            l = Excon.post(File.join(ip,meth), :body => "daemonHost=#{dhost}&daemonPort=#{dport}&filename=#{filename}&password=#{pass}",  :headers => {
                'accept'       => "application/json",
                'X-API-KEY'    => key,
                'Content-Type' => 'application/json',
            })
            puts l.body
        end
end
```
