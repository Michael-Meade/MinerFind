### What is TurtleCoin?
<a href="https://turtlecoin.lol/">TurtleCoin</a> is a decentralized privacy coin. It's purpose is to be used a currency, to allow the users to quickly and easily send money to businesses, friends and family. 
The coins natural privacy features make it so that the user does not have to worry about getting tainted coins that came from a sketch source.
Also it stops companies from using your past purchases or other meta data to build a profile off your consumer habits.



### Payment Id. 
Payment ids are a string of 64 random hex characters that allows the store to identify the buyer after the buyer have sent the payment. 

### integrated addresses
At check out the store will generate a integrated address for the user by combining their TRTL address with the payment id. 
The output is a new TRTL address that the user must use so that the store knows it got their payment.



### The code
```ruby
require 'TurtleCoin'
require 'securerandom'
require 'json'
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
w       = Wallet.new
h       = GenPayId.new("5AC5C5D28F1DE43CA2AB60733478C7E0057ADA34")
addr    = w.address_primary.to_h["address"]
address = JSON.parse(w.create_integrated_address(addr, h.generate_payid))["integratedAddress"]


class ExtractKey
    def get_key(key)
        key.split(//)[24..63].join
    end
end
puts "New address: #{address}\n"

k   = ExtractKey.new
pay = k.get_key("2115a6439a759906db7bdea35ac5c5d28f1de43ca2ab60733478c7e0057ada34")

puts "GPG fingerprint: #{pay}"
```
