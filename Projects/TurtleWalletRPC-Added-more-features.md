<a href="https://github.com/Michael-Meade/TurtleWalletRPC">TurtleWalletRPC</a> is a class written in Ruby that allowst the user to connect to the wallet using RPC.

### auto_on method
The auto on method is located in the module_example.rb file. The goal of this method is to automatically login into a wallet. I have this called in the module_example script so that when the file is caleld the code
will automatically login to the wallet when the file is required_relatived. 

The `TurtleCoin.auto_method` will first call `/status` using the RPC api. If the response of the status shows that an error happened, the code will call the `log_on` method which will use the config file to log into the wallet. 



```ruby
require_relative 'module_example'
TurtleCoin.auto_on
puts TurtleCoin.get_balance
```

### set_node method

By default the set_node method will set the node to: `11898 "TRTLnode.ddns.net"`

### How to use the module
To access the methods in the module, we will have to use require_relative. 

```ruby
require_relative 'module_example'
TurtleCoin.auto_on
puts TurtleCoin.create_addresses(2)
```
An example of a script using the module is above. The scipt will first run the auto_on method. This will log into the wallet if the program is not already logged in.

Next the script will create 2 new address

