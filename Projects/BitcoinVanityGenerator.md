By default, the script will save the created address in the wallets directory. The lib is programmed to save the info with the newly created address as the filename by default. <br> 
### Features
 To create a single address matching a regex.
 ```ruby
 Vanity.regex("1(Meade)")
 ```
 <br>
 If you wanted to save the address info in a certain directory given. If the directory does not exist it will create one with the name you choose.<br> 
 ``` <center> Regex </center> ```
 ```ruby
 Vanity.regex("1(Meade)", "Mike")
 ```
``` <center> Mass Generate </center> ```
```ruby
 Vanity.massGenerate(count, fileToWrite=nil)
```
<br> The code above uses what ever is the number that the variable ```count``` is and will create that many addresses. This does not use any regex it just generates random addresses.  This module also includes the ```fileToWrite``` argument. Which if supplied with a string it will create a new directory and save all the newly created addresses in the directory.<br>


