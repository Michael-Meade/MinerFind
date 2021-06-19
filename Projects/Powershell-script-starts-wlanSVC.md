```powershell
$wlanservice = Get-Service -Name WlanSvc
If ($wlanservice.Status -eq "Stopped") {
    Write-Output "Starting WlanSVC"
    Start-Service -Name WlanSvc
}
```
