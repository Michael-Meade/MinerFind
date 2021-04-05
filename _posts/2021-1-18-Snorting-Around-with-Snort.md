First we have to prep the machine before we install Snort. The instruction says we have to make a temporary. To do this use can use Ubuntu's mkdir command to make the directory. Then we have to use the 
`cd` command to change to that directory. 

```
mkdir ~/snort_src; cd ~/snort_src
```

After that is done, use the following command to install the prerequisites. 
```
sudo apt install -y gcc libpcre3-dev zlib1g-dev libluajit-5.1-dev \
libpcap-dev openssl libssl-dev libnghttp2-dev libdumbnet-dev \
bison flex libdnet autoconf libtool
```

Now that we have installed all the needed prerequisites, we can install snort. We can do download the source code by using the wget command. After the file is downloaded, it will also untar the file becuase we used the `;` o join the commands into one.
It will also change the directory to `daq-2.0.7`
```
wget https://www.snort.org/downloads/snort/daq-2.0.7.tar.gz; tar -xvzf daq-2.0.7.tar.gz; cd daq-2.0.7
```


To start Snort, run the following command. 
```
sudo snort -A console -i lo -u snort -g snort
```
This will tell snort to listen on the loopback interface. 

### Pinging


![The-script](https://i.imgur.com/OplHFRU.png=100x20)
Figure 1, shows the machine pinging itself. 

Figure 1 shows that the IP 192.168.52.143 was pinging itself. Snort also detected that it was using Intertnet Control Message Protocol.


### Fin Scan
![Fin_scan](https://i.imgur.com/mkpxZ0r.png=100x20)
Figure shows the Fin scan in action. 

The Figure above shows what it looks like to Snort when a Fin scan is performed on a machine. Snort is able to detect the scan using the following rule.
```
alert tcp any  any -> any any (msg:"SCAN FIN"; flow:stateless; flags:F,12; reference:arachnids,27; classtype:attempted-recon; sid:621; rev:7;)
```

### Xmas Scan
![xmas_scan](https://i.imgur.com/Y46MsP9.png=100x20)
The XMAS scan will send packets with the FIN, PSH, and URG flags. The Xmas scan got it's name becuase when it is viewed in WireShark, it lights up like a chrismas tree. The image above shows what the scan looks like to Snort. 
The rule that I used to detect this scan looks like this:
```
alert tcp any  any -> any any (msg:"SCAN XMAS"; flow:stateless; flags:SRAFPU,12; reference:arachnids,144; classtype:attempted-recon; sid:625; rev:7;)
```

### TCP SYN 
![tcp_SYN](https://i.imgur.com/nwobyUU.png)

TCP SYN scans are frequently used when scanning a large set of IPs or even IP ranges.  TCP SYN scan is considered a steath scan because it never finishes the threeway handshake. The attackers will send a SYN packet. If the port is opened on the victims machine it will send a SYN/ACK packet back, which tells the attackers that the port open. During a normal three way hanshake, the attacker would send back an AWK packet to tell the other computer that it wants to connect. The image above shows that the snort rule, 
```
alert icmp any any -> any any (msg: "NMAP ping sweep Scan"; dsize:0;sid:10000004; rev: 1;)
```
