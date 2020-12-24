### Orgin Story

I have this discord chat bot named "Moss". One of his features is that he is able to create Bitcoin addresses. I wanted to promte good opsec and make it so that only the user who sent the command is able to see the keys.  The code for moss is public so anyone could see if I was saving the BTC keys.

So I had the idea to use GPG to encrypt the BTC keys with the user's public keys. Basicly I would take the BTC gen code, modfiy it a bit so that instead of saving the keys to file. It would store the information in memory,  encrypt the keys and then send the encrypt keys to the user.


This would means that the user would have to upload their public key to the bot. On my bot Moss, each user has a directory where their settings are stored. Things likes their .dab image that they upload, their todo, movie list,etc. I thought it would be best to have the end user upload their public key to their users directory on moss. 

I decided that the best way to go was to make a wrapper for GPG2. It would allow me to encrypt, import and do basicly anything I wanted with GPG. Plus it would get me fimiliar with GPG, and how it works. 



### The CMD class

This class is probally the most important class. It is the class that will run each of the GPG's arguments. 

Before the CMD class is called, make sure that the class you are working with has inheritanced the CMD class. This can be done by doing the following
```ruby
class Import < CMD
end
```
After that is done create the method you want for example, the Import class looks like this:

```ruby
class Import < CMD
    def import_key(file)
        run("gpg --import #{file}")
    end
end
```

Since we did `< CMD`. We are able to successfully call the CMD method `run("gpg --import #{file}")` which will import a file into the key ring. 


### The Utils Class

The Utils class is where all the utilities scripts are stored. They make life easiy.  The GPG fingerprint is used to indentfiy the public key.



Orginally I had a method that would scrape the users public key username header. But i realized that not every public key has a username field. So I still needed to find a way to link the discord user to the right public key. After doing thinkinga abotu the problem and looking into GPG's  man page. I found that fingerprints would be solve my problem. 

The fingerprint consists of a short hash that represents the public key. The fingerprint method's job in the Util class is to read the users public key file from their profile and use the fingerprint to find their publick key on the keyring. It will the Public key and encrypt the BTC keys with the users public key. This means who ever has access to that private key that belongs to the public key will be able to read the BTC keys.

