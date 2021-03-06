### The problem 

A couple weeks ago my laptop started to act funny. After the computer was booted it was not able to detect any Networks. After some digging on Google, I found out that a service named WlanSVC was not being started when my laptop was turned on. As soon as I turned on the service I was able to see all the networks that are within range and most imporantly I was able to connect to my home network. So everytime I have turned on my Laptop I have to press the windows key + r to open run, scroll down to where it says Wlan AutoConfig and enable the service. This morning I was bored and I was thinking to myself how can I automate the proccess. I have been wanting to learn PowerShell for a while, so I decided to try to make a script that was able to turn on the service. 

### The script
The first thing the snippet does is use the Get=Service cmd-let to get the name of the service,  ( WlanSvc ). The code stores the output of the command as $wlanservice. Next we use a If statement to make sure that the proccess is stopped. 

To get the state of the service we do: `$wlanservice.Status`. This will get the state of the service, if it is running or not. We use the "-eq" comparison operator to check if the status of the service is equal to the string "Stopped". If it is then we use Write-Output to print out a message stating that we are starting wlanSVC. After the message is printed we use the Start-Service to start the service.  Now we should be able to see all the networks that are within range. 


```powershell
$wlanservice = Get-Service -Name WlanSvc
If ($wlanservice.Status -eq "Stopped") {
    Write-Output "Starting WlanSVC"
    Start-Service -Name WlanSvc
}
```
