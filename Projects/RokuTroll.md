<a href="https://michael-meade.github.io/" style='margin-right:20px'>Home</a>
<a href="https://michael-meade.github.io/Projects" style='margin-right:20px'>Projects</a>
#GitHub Link: https://github.com/Michael-Meade/RokuTroll
## Roku Troll
A lib that allows you to control your Roku Tv from your computer. 

## Info 
In order for it to work, you will need to find the IP of your Roku TV. You can find the IP of the remote by running the following command.<br>
```% ncat -u 239.255.255.250 1900 < roku_ecp_req.txt```

## Troll Features
The troll feature was my favorite part of creating it. There are a bunch of things you can do to troll people. Keep in mind that you have to be on the same network as the TV.<br><br><br>

## <center>  Volume Troll </center>
```ruby
Roku.volume_troll(ip, amount)
```
<br>
This feature randomly picks ```0``` or ```1``` from an array. It uses Ruby's .sample feature. This module allows you to pick the number of times that you want to loop through.<br>
If it picks a ```0``` it will turn down the volume. But if it picks a ```1``` than it will turn up the volume.<br><br>

## <center> Reverse & Forward Troll </center>

## <center> </center>


<br>

## <center>Mute Troll</center>
```ruby
Roku.mute_troll(ip, amount)
```
<br>
  This feature will use Ruby's ```rand(1..50)``` method to generate a random number. If the random number is even then it will mute the volume but if it is a odd number it will turn the volume up. This module takes two arguments, ```ip``` and ```amount```.


## <center>Volume Up & Volume Down Troll</center>
```ruby
Roku.volume_up_troll(ip, amount)
```
The module ```volume_up_troll``` takes two arguments, ```ip``` and ```amount```.  This method will turn up the volume the amount that was inputed. 
```ruby 
Roku.volume_down_troll(ip, amount)
```
<br>
There is also a ```volume_down_troll``` that does the same thing but turn the volume down. 
<br>

## Menus
<br>
<center>Control Menu</center><br>
To print the control menu the module below is used.
```Roku.control(ip)```

