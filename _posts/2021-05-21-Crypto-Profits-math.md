


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
