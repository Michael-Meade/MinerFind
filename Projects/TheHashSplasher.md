# About

This is a tool that attempts to determine what type of hash a string is. The program stores all the different hashes it is able to detect in a JSON file. Which makes it 
easy for new hashes to be added bost manually and programmatically. The name HashSplasher means nothing really, its just that splash rhymes with hash.  The regexs are stored in a JSON file 
with the name regex.json.


# How to run?
```HashSplash.new("7f83b1657ff1fc53b92dc18148a1d65dfc2d4b1fa3d677284addd200126d9069").identify```<br>
This tool is not perfect and sometimes will detect multiple types of hashes. This is by design because I wanted a tool that might be useful for CTF. So it will keep going 
untill it runs out of regex files in the `regex.json`
