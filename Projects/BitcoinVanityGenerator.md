### Background
Bitcoin addresses uses secp256k1 curve. <br>
```ruby
# Creates the variable curve withe the Curve Key
curve = OpenSSL::PKey::EC.new('secp256k1')
curve.generate_key
private_key_hex = curve.private_key.to_s(16)
public_key_hex  = curve.public_key.to_bn.to_s(16)
```
<br>
To create the ```publicKeyHash``` varaible we use the following functions to generate the public key hash. <b>
  ```ruby
  def public_key_hash(hex)
    rmd160(sha256(hex))
  end
  def rmd160(hex)
    Digest::RMD160.hexdigest([hex].pack("H*"))
  end
  def sha256(hex)
    Digest::SHA256.hexdigest([hex].pack("H*"))
  end
  ```
  <br>
