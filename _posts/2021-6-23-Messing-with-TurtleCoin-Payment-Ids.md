---
layout: post
title:  "Messing-with-TurtleCoin-Payment-Ids"
tags: [ TurtleCoin, paymentid ]
---


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
pay = k.get_key(h.generate_payid)

puts "GPG fingerprint: #{pay}"
```
First thing the code does is load the json gem. The code also requires the Turtlecoin library I created.
The first class in the code is the GenPayId class. This class takes one instance argument, the user's fingeroprint to their public key.
The hex method generates a random hex string that will be added to the user's fingerprint. The `generate_paymentid` method will first split up the randomly generated hex string so that each character is a element in an array. The `//` is what turns the hex string into the array. In Ruby the first element in arrays start at 0. Since we start at 0, 64 is really 63. We know that the payment id has to be 64 characters so we subtract 64 ( which is really 63) from the length of the fingerprint. The outcome of that number should be equal to 40.  Next we use the .join method to turn the array back into a string. The result of all removes the last 40  characters.  The last thing the generate_payid does is add the fingerprint to the end of the paymentid and returns it.


The `ExtractKey` class is used extract the fingerprint from the payment id. The `get_key(key)` method takes on one argument which is the payment id. The method first will split up the string so each characters is its own element in the array. Next the code will get start at the 24th character in the payment id and end at the 64th character. It extracted the fingerprint from the payment id. One thing though, the wallet-api converts the fingerprint to all lowercase. So it is a must that the last thing that should be done is to use Ruby's built in .upper method which will turn the string into all uppercase characters. The store will would need to implement a system where the fingerprint of the user is compared to the fingerprint that was extracted from the payment id. 


### Hexspeak

The TurtleCoin wallet api will only accept payment IDS that are hex. According to <a href="https://simple.wikipedia.org/wiki/Hexadecimal">Wikipedia</a> valid hex charcters are  0,1,2,3,4,5,6,7,8,9 and A, B, C, D, E, F
    

<a href="https://en.wikipedia.org/wiki/Hexspeak">HexSpeak</a> is a variant of English that tires to makes words out valid hex character. 
<br><br>

A example of Hex speak would be: `c105e`. Which is close in normal english.

Below is some of the code that can be used to create a hex speak payment ID.
```ruby
    require 'securerandom'
class HexSpeak
    def pick_speak
        File.readlines("hexspeak.txt").sample
    end
    def count(c = 0)
        pick = []
        for i in 0..c.to_i
            pick << pick_speak.strip
        end
    return pick.join
    end
end

pay  = HexSpeak.new.count(6)
hex  = SecureRandom.hex(32)
puts hex.split(//)[0..63 - pay.length.to_i ].join + pay
```

The contents of hexspeak.txt can be downloaded by running the following command.
`wget -O hexspeak.txt https://gist.githubusercontent.com/gabrielfalcao/c942f6602401f0697c206e30f0aa4bad/raw/768da56222c1ad3439b3a54879a220aaa699855f/hexspeak`



