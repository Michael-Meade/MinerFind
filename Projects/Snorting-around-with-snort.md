---
title: Snorting Around with Snort
---
First we have to prep the machine before we install Snort. The instruction says we have to make a temporary. To do this use can use Ubuntu's mkdir command to make the directory. Then we have to use the 
`cd` command to change to that directory. 

Before downloading DAQ or Snort, make sure that you use the most current versions. To check visit <a href="https://www.snort.org/downloads">here</a>

```
mkdir ~/snort_src; cd ~/snort_src
```

After that is done, use the following command to install the prerequisites. 
```
sudo apt install -y gcc libpcre3-dev zlib1g-dev libluajit-5.1-dev \
libpcap-dev openssl libssl-dev libnghttp2-dev libdumbnet-dev \
bison flex libdnet autoconf libtool
```

Now that we have installed all the needed prerequisites, we can install snort. We can do download the source code by using the wget command. After the file is downloaded, it will also untar the file becuase we used the `;` to join the commands into one.  It will also change the directory to `daq-2.0.7`


DAQ is needed for snort to work because it allows snort to "make abstracts calls to packet capature libraries
```
wget https://www.snort.org/downloads/snort/daq-2.0.7.tar.gz; tar -xvzf daq-2.0.7.tar.gz; cd daq-2.0.7
```

When I installed snort on a clean Ubuntu iso, autoconf was not installed. To install autoconf use this command:

```
sudo apt install autoconf
```
Next we have to run this command. Autoconf is a neat tool that will create scripts that will automatically configure softwares like Snort so we can easily compile the program on any Posix-like OS. 
```
autoreconf -f -i
```

Next we enter the 
```sudo ./configure && sudo make && sudo make install
```
These commands will compile and install DAQ. 

Now that we have installed DAQ, we can now install Snort. The first command we have to use is the change directory command. This wil allow us to go back a directory. 

```
cd ../
```

First we have to use WGET to download the Snort gz. 
```
wget https://www.snort.org/downloads/snort/snort-2.9.17.tar.gz
```
Now use the tar comand to  untar the file. We also use `;` so we can join togetg 

```
tar -xvzf snort-2.9.17.tar.gz; cd snort-2.9.17
```
Now we have to make the file, which preps the machine seo it can be installed quickly, we have to configure and compile the package.

```
./configure --enable-sourcefire && make && sudo make install
```


### Credits to:

- https://upcloud.com/community/tutorials/install-snort-ubuntu
- https://www.gnu.org/software/autoconf/manual/autoconf-2.67/autoconf.html#Introduction
