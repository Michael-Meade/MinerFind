


<meta name="keywords" content="Cryptocurrency profits formula" />


## The formula 
The formula that will be used in this project is ( current_price - price_bought_at ) * amount. 
As of right now, Bitcoin is worth $37,121.70. Lets say that we bought Bitcoin when it was $10,000. The amount of Bitcoin that we bought is .1000.

The formula would look like this: 
( 37,121.70 - 10,000 ) * .1000 

The math equation above equals to $2,712.10!


```ruby
require 'bigdecimal'
class Crypto
    def initialize(current_amount, bought_price, amount)
        @current_amount = current_amount
        @bought_price   = bought_price
        @amount         = amount
    end
    
    def calc
        BigDecimal(@current_amount.to_i - @bought_price.to_i ) * @amount
    end
end
c = Crypto.new(37121.70, 10000, 0.1000)
puts c.calc.to_f
```
With the help of the <a href="https://ruby-doc.org/stdlib-2.5.1/libdoc/bigdecimal/rdoc/BigDecimal.html">BigDecimal gem</a> we are able to use numbers that are decimals with ease.
The number '37121.70' is the current price of Bitcoin in USD. The '10000' number is the price that we bought the coins at. This number is also in USD. The '0.1000' number is the amount of coins that we bought. 

The numbers are used as values to the instace variables: current_amount, bought_price and amount, respectively.

The calc method is what we need to call for the class to do the math. It will take the instance variables and do the math and return the results. Note that the we used .to_f so that it will put the decimal in the right position.

I plan on adding a feature on Moss, my Discord bot that would allow me and other users to store the price bought & the amount of coins bought. Instead of having the user have to input the current price, the code will use a API to get the current price of the coin. 

```ruby
class GetPrice
    def initialize(coin_name)
        @coin_name = coin_name
    end
    def price
        r = HTTParty.get("https://min-api.cryptocompare.com/data/price?fsym=#{@coin_name}&tsyms=USD").body
    JSON.parse(r)["USD"]
    end
end
```

The GetPrice class has one instance variable called 'coin_name'. The code is not meant to just calculate a certain coin, but many coins. The 'coin_name' instance variable is used to tell the API whatv coin we want to get the price for. The 'price' method is what is called to get the price of the coin that the user wants to lookup. 


The 'Crypto' class and the 'GetPrice' class work together to return the profits. I personally like to wrap both the classes into a module so that only one method has to be called to carry out the task.

```ruby
module CryptoCalc
    def self.btc(bought_price, amount)
        price = GetPrice.new("BTC").price
        puts Crypto.new(price.to_i, bought_price, amount ).calc.to_f
    end
end

```
The module we created is called 'CryptoCalc'. The purpose of this program is to be used to get the profits of cryptocurrencies that was invested. Any investor will tell you that it is a bad idea to only invest in one coin. So the program was designed to get the price of other coins aswell. All the programmer has to do is to create another method with in the module for that coin. The first thing that the code does is instantiate the 'GetPrice' class, call the 'price' method and  store it as the variable price. Doing this will give us the current price of BTC. Next the code will instantiate the Crypto class, take two arguments ( bought_price & amount) and call the 'calc' method which will take the current price, the 'bought_price' & the amount to calculate the profits. 
