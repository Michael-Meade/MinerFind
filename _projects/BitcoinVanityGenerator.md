---
layout: projects
title:  "Inside Linux Mining malware "
by:     "Michael Meade"
---
<br>
By default, the script will save the newly created address in the "wallets" directory. The lib is programmed to save the information into a txt file with the BTC address as the file name. <br> 
### Features
### <center> Single Regex </center>
 To create a single address matching a regex.
 ```ruby
 Vanity.regex("1(Meade)")
 ```
 <br>

 
### <center> Regex </center> 
 <br>
 ```ruby
 Vanity.regex("1(Meade)", "Mike")
 ```
 <br>
 
### <center> Mass Generate </center>
```ruby
 Vanity.massGenerate(count, fileToWrite=nil)
```

<br>
<br>The count variable determines how many addresses that you want to create. This module does not use any regex it just generates random addresses.  This module also includes the ```fileToWrite``` argument. Which will save all the generated information inside the directory.  It will still create a text file with the newly created wallet information inside.
<br>


## <center> Mass Regex Generate </center>
```
Vanity.regexFiles("regexFile", 3, fileToWrite=nil)
```
This will take the inputed file and generate as many addresses that the ```count``` parameter was given. Everytime it generates a address the script will check if the address matches any of the regexs in the given file. 
