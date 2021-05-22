


<meta name="keywords" content="Cryptocurrency profits formula" />


## The formula 
The formula that will be used in this project is ( current_price - price_bought_at ) - amount. 
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
    def amount
        @amount
    end
    def current_amount
        @current_amount
    end
    def bought_price
        @bought_price
    end
    def calc
        BigDecimal(current_amount.to_i - bought_price.to_i ) * amount
    end
end
c = Crypto.new(37121.70, 10000, 0.1000)
puts c.calc.to_f
```
