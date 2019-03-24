<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
## Roku Troll
A lib that allows you to control your Roku Tv from your computer. 

## Info 
In order for it to work, you will need to find the IP of your Roku TV. You can find the IP of the remote by running the following command.<br>
```% ncat -u 239.255.255.250 1900 < roku_ecp_req.txt```

## Troll Features
The troll feature was my favorite part of creating it. There are a bunch of things you can do to troll people. Keep in mind that you have to be on the same network as the TV.<br><br><br>

<center>  Volume Troll </center>
This feature randomly picks ```0``` or ```1``` from an array. It uses Ruby's .sample feature. This module allows you to pck the amount of times that you want to loop through.<br>
If it picks a ```0``` it will turn down the volume. But if it picks a ```1``` than it will turn up the volume.
