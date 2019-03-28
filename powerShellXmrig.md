I found this sample on hybrid-analysis.com.  First thing it does is get some information about the infected computer. 
```powershell$osCheckMinor = [System.Environment]::OSVersion.Version | Select -Expand Minor;
$osVersion = "$osCheckMajor" + '.' + "$osCheckMinor";
$poshVersion = $PSVersionTable.PSVersion.Major;
```


I am not familiar with powershell so I decided to run and print the code above. When I ran the code and printed the variable ```$osCheckMinor``` the output was zero. <br>
When I printed the variable  ```$osVersion = "$osCheckMajor" + '.' + "$osCheckMinor";``` the results where ```.0```.<br>
 
The code snippet below is the part of the code that creates a random string with the variable name ```$peName```. After it generates the random number the code will append ```.exe``` to the end of the string. <br>

![Octocat](https://i.imgur.com/Fa5Qtra.png=100x20)
