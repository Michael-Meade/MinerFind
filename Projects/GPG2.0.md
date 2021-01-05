 {% seo %}
### GPG2
.|.



### Orgin Story
I have this discord chatbot named "Moss". One of his features is that he can create Bitcoin addresses. I wanted to promote good opsec and make it so that only the user who sent the command can see the keys. The code for Moss is open-sourced, so anyone could see if I was saving the BTC keys.
So I had the idea to use GPG to encrypt the BTC keys with the user's public keys.
 I took the Bitcoin generating code that I coded a few years ago. I then modified it so that instead of saving the keys to a file it will encrypt the BTC keys with the user's public key. 


It would store the information in memory, encrypt the keys, and then send the encrypted output to the user.
This means that the user would have to upload their public key to the bot. On my bot Moss, each user has a directory where their settings are stored. Things like their .dab image that they upload, their todo, movie list, etc. I thought it would be best to have the end-user upload their public key to their user's directory on moss.
I decided that the best way to go was to make a wrapper for GPG2. It would allow me to encrypt, import, and do anything I wanted with GPG. Plus it would get me familiar with GPG, and how it works.
The CMD class
This class is probably the most important. It is the class that will run each of the GPG's arguments.
Before the CMD class is called, make sure that the class you are working with has inherited the CMD class. This can be done by doing the following
```ruby
class Import < CMD
end
```
After that is done create the method you want, for example, the Import class looks like this:
```ruby
class Import < CMD
    def import_key(file)
        run("gpg --import #{file}")
    end
end
```
Since we did < CMD. We can successfully call the CMD method run("gpg --import #{file}") which will import a file into the keyring.

### The Utils Class
The Utils class is where all the utility scripts are stored. They make life easy. The GPG fingerprint is used to identify the public key.
Originally I had a method that would scrape the user's public key username header. But I realized that not every public key has a username field. So I still needed to find a way to link the discord user to the right public key. After thinking about the problem and looking into GPG's man page. I found that fingerprints would solve my problem.
The fingerprint consists of a short hash that represents the public key. The fingerprint method's job in the Util class is to read the user's public key file from their profile and use the fingerprint to find their public key on the keyring. It will encrypt the BTC keys with the user's public key. This means whoever has access to that private key that belongs to the public key will be able to read the BTC keys.

### The Encrypt Class
There are two ways to encrypt messages with GPG2.0. The first way is with the `encrypt_msg(text_to_encrypt)` method.This method encrypts text. This method uses gets the users public key and then encrypts text with the public key. It will return the encrypted text. 

There is also a way to encrypt a file with PGP. The method that does this is: `Encrypt.encrypt_file(file_to_encrypt, public_key_path)`
 
 The encrypt method also has a setting named: `fprint_settting` by default this setting is set to true.  Last night on 12/27/2020 I realized that the way I was doing it was stupid and made no sense. There is still a way to use read the users public key to get the fingerprint.
 
 
 The logic is: 
 If `fprint_setting` is not true (false) then
 it will assume that `publickey_name` is the fingerprint of the users public key. Next it will encrypt the text or file with what ever
 fingerprint was given in the publickey_name argument. But the programmer also has the options to read the users public key and create a fingerprint with that. 
 
 But by default the `fprint_stting` is set as true. One way to implment this would be to keep the fingerprint of the users in a JSON file. When the user needs to encrypt soemthing. The script will read the config file, get the fingerprint and then encrypt what ever it needs to  encrypt. 
 




Now when the user uploads their puiblic key, the bot will also create a fingerprint of the users public key. Save that hash in the user's config file. 
This can be turned off if the programmers wants to by using the following code:

```ruby
Encrypt.new.encrypt_msg(text_to_encrypt, pubkey_name, false)
```


The following are examples uses:
```ruby
Encrypt.new.encrypt_file("encrypt Me", "path_to_publickey.pub")
```
```ruby
Encrypt.new.encrypt_msg("happy Xmas", "path_to_publickey.pub")
```
