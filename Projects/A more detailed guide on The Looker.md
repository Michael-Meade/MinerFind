### What is the looker?
The looker is a tool that is able to extract information out of non compiled scripts. It might work with compiled 
programs too if the author did not remove the strings. The story of this project that I would search  <a href="https://www.hybrid-analysis.com/">Hybrid-analysis</a> for non compiled samples like 
vbs, sh, py, perl. This is where I found most of the samples that I have written about. At first I was doing it manually. Most the samples also downloaded other files and did stuff with them, so I woudld have
a bunch of tabs open in Sublime. A bunch of different directories and files. It was starting to get a mess and becoming hard to go back to the task after taking a break. 

I thought to myself that there has to be a way to automate the proccess. The looker is the product of that idea. 

Each functionality has different class. This is so that the person running the program can decide what functionality they want to use on the sample. It would
also make it easier to add functionality to the program later without making a mess. 



The orginal post about this project can be found <a href="https://michael-meade.github.io/Projects/The-Looker.html">here</a>

### Running main.rb
```ruby
ruby main.rb d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh
```
This will create a new directory in the output directory. It will create a new directory named `d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh`.
All the data and files that was extracted from the sample will be stored here.
The program wil store all the data that it gathered from the sample in the file named `d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh.txt`

The snippet below shows what the contents of the file `d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh.txt`.

```
[ FILE ]
d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh: Bourne-Again shell script, ASCII text executable

[ URLS & IPS ]
 114.114.114.114
8.8.8.8
127.0.0.1
0.0.0.0
0.0.0.0
100.100.25.3
0.0.0.0
100.100.25.4
0.0.0.0
185.164.72.119
0.0.0.0
0.0.0.0
0.0.0.0
185.71.65.238
140.82.52.87
45.76.122.92
51.38.191.178
51.15.56.161
158.69.133.18
104.248.4.162
89.35.39.78
107.174.47.156
83.220.169.247
51.38.203.146
144.217.45.45
107.174.47.181
176.31.6.16
46.243.253.15
176.31.6.16
200.68.17.196
188.209.49.54
181.214.87.241

http://update.aegis.aliyun.com/download/quartz_uninstall.sh
http://update.aegis.aliyun.com/download/uninstall.sh
http://xia.vzboot.com/alddur
http://xia.vzboot.com/my.sh
http://xia.vzboot.com/s68.sh
http://xia.vzboot.com/sso.sh

[ INTRESTING STRINGS ]
 cron

monero

xmr

wget

curl


[ FILE HASH ]
 MD5: 6d81e06505bbeb1c34b8127dae540af2

```
The first header in the file is the 'file' header. This is where information about the type of file is stored. In the example above the file is a `Bourne-Again shell script`.

The next header is all the IPS and URLS that was found in the sample. 

The program has a feature that allows the user to create a list of intresting words or strings that they want to look for in the sample. 

The last header of the file is the file hash header. It is important to get the hash of the sample. This is because it allows other people to find the same sample and makes sure that the sample was not changed. Changing one thing in the file would cause the hash to be a different.
