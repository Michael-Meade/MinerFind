### The problem 

A couple weeks ago my laptop started to act funny. After the computer was booted it was not able to detect any Networks. After some digging on Google, I found out that a service named WlanSVC was not being started. As soon as I turn on the service I was able to see all the networks that are within range and most imporantly able to connect to my home network. So everytime I have turned on my Laptop I have to press the windows key + r to open run, scroll down to where it says Wlan AutoConfig and enable the service. This morning I was bored and I was thinking to myself how  can I automate the proccess. I have been wanting to learn PowerShell for a while, so I decided to try to make a script that was able to turn on the service. 


### The script
The first thing it does it use the Get=Service cmd-let to get the name of the service,  ( WlanSvc ). It stored the output of the command as $wlanservice. Next we use a If statement to make sure that the proccess is stopped. 

By using the variable #wlanservice we are able to add .Status to it to only get the state of the service. If the state of the service is equal to Stopped then the code will print out "Starting WlanSVC" and use the Start-Service cmdlet to start the service.


```powershell
$wlanservice = Get-Service -Name WlanSvc
If ($wlanservice.Status -eq "Stopped") {
    Write-Output "Starting WlanSVC"
    Start-Service -Name WlanSvc
}
```
