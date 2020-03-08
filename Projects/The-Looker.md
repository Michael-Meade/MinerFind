# Purpose
The purpose of this project is to make automate the proccess of reverse engineering scripts and binary. 
. This project is meant to be ran on Linux operating system. The-Looker uses some of the Linux built in commands.
It currently has the following funcitonaly:
  [+] Runs and save the output from the strings command<br>
  [+] It could run the file command aganist the testing file<br>
  [+] The ability of detecting certain strings. The user can add strings anytime they want.<br>
  [+] The script also hashes the input file and saves the output. <br>
  [+] It can also detect and save possible cryptocurrency addresses.<br>
  [+] Detect and save possible URLS.<br>
  [+] Detect possible SSH keys<br>
  <br>
  The goal of this script was to make it easiy for the user to save all the information about the file in question in one spot that will make it 
  easier to look and write reports about. It is also written in a module way,  that would allow users to easily make it cutsomized.  
  <br>
  # Detecting Crytocurrency Addresses
  First thing the user should do if, they want to use the crypto class is make sure that it is required in the
  script. This can be done by putting the following on the top of the script. ```require_relative 'lib/crypto'```<br>
  
  There are a couple different ways that the crypto class could be used. One way is to run all the crypto methods. This can be done by using 
  the ```Crypto.all(file_name)``` method. If the user was to add any new method, they might want to cosnider also putting the new method in inside the
  all method. This is meant to make it easier and cleaner to run all the different type of crypto dectors. 
  
  If the user only wants to detect crypto currencies address, then the ```Crypto.crypto_currency(file_name)``` method could be used. 
  By default this will run the ```Crypto.detect_bitcoin(file_name)``` and the ```Crypto.detect_monero(file_name)``` method. <br>
  
  
  The ```Crypto.detect_ssh(file_name)``` method is used to detect SSH keys that might be inside the scripts.
  
   # The Commands class
   
   The file command is basicly the [file comamnd](http://man7.org/linux/man-pages/man1/file.1.html). When the ```Command.file_command(file_name)``` method is used
   it will run the file command against the file and save the foutput in the file's output directory.  If the method detects that the file is dynamic linked it will run
   the [ldd](http://man7.org/linux/man-pages/man1/ldd.1.html) command and saved the ouput.
   
   ```Commands.hash_file(file_name)``` method will hash the file in [md5](https://tools.ietf.org/html/rfc1321) and add the output to the file's output folder.
   
  The ```Commands.strings_command(file_name)```  method will run the [strings command](https://linux.die.net/man/1/strings), by default it will save the output into a file's directory with the filename strings.txt
  There is another method named, ```Commands.detect_strings(file_name)``` that could be used with the command above. In the ```lists``` directory, the user can create a filenamed ```strings```. The user 
  could use this file to detect certain strings that they might be looking for. 
  
  
  The method ```Crypto.detect_urls(file_name)``` uses a regex to detect URLs or IPS that be inside the script. This script works best with uncompiled files.
