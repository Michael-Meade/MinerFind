### TurtleCoin
<a href="https://turtlecoin.lol/">TurtleCoin</a> is a privacy focused coin that was created on December 09, 2017. 
Unlike Bitcoin, the blockchain is private, meaning no one that does not have the view key is able to see the transcations. On October 20th, 
<a href="https://blog.turtlecoin.lol/archives/trtl-v2/">TurtleCoin</a> announced that they are planning to relaunch with version2 of TurtleCoin. 
This project is a wrapper for  <a href="https://turtlecoin.github.io/wallet-api-docs/">wallet-api</a>. It's goal is to make it easy to use the TurtleCoin's api wallet.



The code can be found <a href="https://github.com/Michael-Meade/TurtleWalletRPC">here</a>
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
and put that information in the body of the request. There is also a get method and put method too.
```ruby
def post(meth, j = nil)
    l = Excon.post(File.join(ip,meth), :debug_request => true, :debug_response => true, :body => j,  :headers => {
        'accept'       => "application/json",
        'X-API-KEY'    => key
    }).body
end
```

### The Wallet Class
Like the config class, the Wallet Class will Inherit the HTTP class. This is needed so that we can call the get, post, put methods. Without it we would not be able to call it. This is where we use the Wallet API end points to do stuff. 

Here is a quick list of what is possible:
- open wallet
- create addresses
- list addresses
- import addresses
- get node information
- save the wallet state
- get an address balance
- get the primary address
- get the status of the wallet
- get the addresses keys
- get the shared private key
- get keys mnemonic


### How to use


## List Addresses
```ruby 
Wallet.new.list_addresses
```
## Open Wallet
To use a wallet you have to open it first.
```ruby
Wallet.new.open_wallet
```
## Addresses Import
This will import a subwallet with the given private spend key. By default the `scanHeight` is 300000.
```ruby
Wallet.new.addresses_import("3e2ced750b75cb01b85bd83a0f0a45623c51e6ba2debc506a1a3b71577ae0408")
```

## Address Primary
Get the primary address of the wallet.
```ruby
Wallet.new.address_primary
```

## Get Address Balance
An TRTL address needs to inputed. 
```ruby
Wallet.new.balance("TRTLuxiuS26Budy7hQusmtW6T19gbfTnLiLSpXgxwFLDVaAq4JwD9h9A9HJr2ZhWwoBc8hkbEerBHXPDZq9MHSfQ3Qs5AEHRVtc")
```

## Balances
Gets all the wallets Balances
```ruby
Wallet.new.balances
```

## Key Mnemonic
Gets the mnemonic seed for the address
```ruby
Wallet.new.keys_mnemonic("TRTLuxiuS26Budy7hQusmtW6T19gbfTnLiLSpXgxwFLDVaAq4JwD9h9A9HJr2ZhWwoBc8hkbEerBHXPDZq9MHSfQ3Qs5AEHRVtc")
```


## Keys
Gets the wallet containers shared private key
```ruby
Wallet.new.keys
```

## Keys Address
Gets the public & private spend key for a given address. It can't be used with a view only wallet.
```ruby
Wallet.new.keys_address("TRTLuxiuS26Budy7hQusmtW6T19gbfTnLiLSpXgxwFLDVaAq4JwD9h9A9HJr2ZhWwoBc8hkbEerBHXPDZq9MHSfQ3Qs5AEHRVtc")
```

## Status
Get Wallet Status
```ruby
Wallet.new.status
```


## Set Node
Set the node
```ruby
Wallet.new.set_node("127.0.0.1", "1234")
```

## Save 
Wallet State
```ruby
Wallet.new.save
```

## Create Addresses
```ruby
Wallet.new.create_addresses
```


### Examples

## Creaet new TRTL addresses and save in a JSON file.
Creates a new TRTL address and saves in a JSON file.
```ruby
wallet = Wallet.new.create_addresses
File.open("wallet2.json", "w") { |file| file.write(wallet) }
```

## List TRTL Addresses
```ruby
t = Wallet.new
t.list_addresses.each do |addr|
    puts addr
end
```
