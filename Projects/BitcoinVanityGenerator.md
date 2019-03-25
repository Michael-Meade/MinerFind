By default the script will save the created address in the wallets directory. The lib is programed to save the info with the newly created address as the filename by default. <br> 
### Features
 To create the a single address matching a regex.
 ```ruby
 Vanity.regex("1(Meade)")
 ```
 <br>
 If you wanted to save the address info in a certain directory given. If the directory does not exist it will create one with the name you choose.<br> 
 
 ```ruby
 Vanity.regex("1(Meade)", "Mike")
 ```
```ruby
 massGenerate(count, fileToWrite=nil)
```
