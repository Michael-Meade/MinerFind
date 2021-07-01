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

Next the script will create 2 new address. 


### Checks Wallet Info
```ruby
require_relative 'module_example'
print("=========Wallet=========\n")
puts TurtleCoin.get_balances
print("=========Info=========\n")
print("Address Count: " + TurtleCoin.address_count.to_s)
print("\n")
print("Saving addresses in addresses.txt...\n")

status = TurtleCoin.status

j = JSON.parse(status)


print("\n=========Status=========\n")
print("Wallet Block Count: #{j["walletBlockCount"]}\n")
print("Local Daemon Block Count: #{j["localDaemonBlockCount"]}\n")
print("Network Block Count: #{j["networkBlockCount"]}\n")
print("Peer Count: #{j["peerCount"]}\n")
print("Hash Rate: #{j["hashrate"]}\n")
print("View Wallet: #{j["isViewWallet"]}\n")
print("Sub Wallet: #{j["subWalletCount"]}\n")


TurtleCoin.save_addresses
```

### Payment Id 
```ruby
require_relative 'module_example'
require 'set'
class ExtractKey
    def get_key(key)
        key.split(//)[24..63].join
    end
end
class DeletePayment
    def initialize(payment_id)
        @payment_id = payment_id
        read        = File.read("waiting_payment.txt")
        File.open('waiting_payment.txt', 'w') do |out_file|
            File.foreach('waiting_payment.txt').with_index do |line,line_number|
                out_file.puts line if not read.match?(@payment_id)
            end
        end
    end
end
class AddPayment
    def initialize(fingerprint)
        @fingerprint = fingerprint
        File.open(File.join("paid.txt").to_s, 'a') { |file| file.write("\n" + @fingerprint) }
    end
end
puts "starting..."
while true
    read = File.read("waiting_payment.txt").split
    p read
    TurtleCoin.transactions["transactions"].each do |l|
        if read.include?(l['paymentID'])
            k       = ExtractKey.new
            finger  = k.get_key(l['paymentID'])
            puts "Deleting payment id from waiting_payment"
            DeletePayment.new(l['paymentID'])
            puts "Payment finished. -- adding to paid.txt"
            AddPayment.new(finger)
        end
    end
    sleep 10
end
```
The script above should be ran by a cronjob. When a payment is created, the payment id is saved in a file. This script reads the contents of that file and checks to see if the wallet has received a transcation that contains the payment id. It wil remove the payment id from the waiting list and add it to the paid.txt.

The code uses the fingerprint of their GPG public key. The code will generate a random string of hex, add the users public key at the end of the string. Next the code will create a integrated wallet with the payment id. 

### The main script
```ruby 
require 'securerandom'
require 'json'
require 'TurtleCoin'

class GenPayId
    def initialize(fingerprints)
        @fingerprints = fingerprints
    end
    def fingerprints
        @fingerprints
    end
    def hex
        SecureRandom.hex(32)
    end
    def generate_payid
        payid = hex.split(//)[0..63 - fingerprints.length.to_i ].join
    return payid + fingerprints
    end
end




class SavePayment
    def initialize(payment_id)
        @payment_id = payment_id.downcase
        puts "PPPP> #{@payment_id}"
        File.open(File.join("waiting_payment.txt").to_s, 'a') { |file| file.write("\n" + @payment_id) }
    end

end
w       = Wallet.new
payid   = GenPayId.new("5AC5C5D28F1DE43CA2AB60733478C7E0057ADA34").generate_payid
addr    = w.address_primary.to_h["address"]
address = JSON.parse(w.create_integrated_address(addr, payid))["integratedAddress"]
puts "#{payid}"
puts "New address: #{address}\n"
SavePayment.new(payid)
```
The first thing the script does is to create an instance of Wallet and store it as the variable w. Next we use the GenPayId to create a random hex, the class will then append the users fingerprint to the random hex. Next we use the wallet api to get the address of the wallet. After that is finished the code wall use the newly generated payment id and the address we obtained from the wallet to generate an integrated. The results will be used by the end user to pay for the service. The last thing the code does is use the SavePayment class to save the payment. The code above this will use this file to check for incomming transcations.

A more detailed look can be found <a href="https://michael-meade.github.io/2021/06/23/Messing-with-TurtleCoin-Payment-Ids.html">here.</a>
