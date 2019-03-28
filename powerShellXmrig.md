I found this sample on hybrid-analysis.com.  First think it does is get some information about the infected computer. 
```
$osCheckMinor = [System.Environment]::OSVersion.Version | Select -Expand Minor;
$osVersion = "$osCheckMajor" + '.' + "$osCheckMinor";
$poshVersion = $PSVersionTable.PSVersion.Major;
```
<br>
