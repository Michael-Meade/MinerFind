### Orgin Story

I have this discord chat bot named "Moss". One of his features is that he is able to create Bitcoin addresses. I wanted to promte good opsec and make it so that
not everyone who is on the discord is able to see the bitcoin keys. So I had the idea to use GPG to encrypt the keys with the users public keys. This would means that the user
would have to send the bot their public key. So I had to also find a way to import their Public key into my keyring, I would have to also encrypt the keys without having the keys 
be saved on disk. Basicly I had to join together a coulple of different projects. First I had to modify the BTC Address generating script I made a year or so earlier so that it does 
not save the file on disk. After that I had to make a wrapper for GPG. Basicly the script will asume that that GPG is installed. It will use ruby to run GPG commands if as a person typed it out.
After doin all that and getting to work as I wanted I thought I would create a whole project where I code a GPG wrapper


### The CMD class

This class is probally the most important. It is the class that will run each of the commands. 

Before the CMD class is called, make sure that the class you are working with has inheritance the CMD class. This can be done by doing the following
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
