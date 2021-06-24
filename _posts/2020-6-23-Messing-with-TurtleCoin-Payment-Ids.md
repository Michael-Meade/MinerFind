### What is TurtleCoin?
<a href="https://turtlecoin.lol/">TurtleCoin</a> is a decentralized privacy coin. It's purpose is to be used a currency, to allow the users to quickly and easily send money to businesses, friends and family. 
The coins natural privacy features make it so that the user does not have to worry about getting tainted coins that came from a sketch source.
Also it stops companies from using your past purchases or other meta data to build a profile off your consumer habits.



### Payment Id. 
Payment ids are a string of 64 random hex characters that allows the store to identify the buyer after the buyer have sent the payment. 

### integrated addresses
At check out the store will generate a integrated address for the user by combining their TRTL address with the payment id. 
The output is a new TRTL address that the user must use so that the store knows it got their payment.


### The idea

<a href="https://gnupg.org/">GPG</a> is a wonderful tool that allows people to communicate securely. If person A wanted to send person B a message, they would use person's B public key to encrypt the message. Only person B or who ever has access to person's B private key is able to read the message. People might be able to see that person A and person B communicated together but will not be able to see what person A said to person B. Also if their opsec is tight no one will be able to know who person A or B was. When using GPG it is important to use a different key for each person they communicate with. That way if someone was able to figure out who owns the private key of a certain public key, then they will know EVERYONE that has communicated with them might be at risk. 

Public keys are pretty large and hard to recognized. So GPG has something called fingerprints, these are used to identify the public key. It is a smaller hash that represents the public key. 
    
    
    
 The idea was to create a random strings of hex. Part of the random strings of hex is removed and replaced with the fingerprint of the users public key. This will allow the store to identify the user buy their fignerprint. The store might have it so when they create an account the user has to upload their public key. The store could use the public key to encrypt sensitive information that it would send to the user. This will make it nearly impossbile for the information to be read by the wrong person. 
    
After the store created the new hex the store will need to create the actually TRTL address that the user will paywith. I used my Ruby library 
to create the integrated addresses. After the integrated addresses is created the user would be redirected to a new page that they can use to pay. 
The hex that is used as the payment looks random but it acutally hides the public key in plain sight. 
    
Now the store will have to look at their incomming transcations to their wallet, read the transcations payment id, and extract the user's GPG fingerprint from the payment id. The store now knows that the user has paid for the item and can release the item or mark for shipping. 
    
    
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
class ExtractKey
    def get_key(key)
        key.split(//)[24..63].join
    end
end

w       = Wallet.new
h       = GenPayId.new("5AC5C5D28F1DE43CA2AB60733478C7E0057ADA34")
addr    = w.address_primary.to_h["address"]
address = JSON.parse(w.create_integrated_address(addr, h.generate_payid))["integratedAddress"]


puts "New address: #{address}\n"

k   = ExtractKey.new
pay = k.get_key("2115a6439a759906db7bdea35ac5c5d28f1de43ca2ab60733478c7e0057ada34")

puts "GPG fingerprint: #{pay}"
```
First thing the code does is load the json gem. The code also requires the Turtlecoin library I created.
The first class in the code is the GenPayId class. This class takes one instance argument, the user's fingeroprint to their public key.
The hex method generates a random hex string that will be added to the user's fingerprint. The `enerate_paymentid` method will first split up the randomly generated hex string so that each character is a element in an array. The `//` is what turns the hex string into the array. In Ruby the first element in arrays start at 0. The code now gets the length of the fingerprint and removes the 
