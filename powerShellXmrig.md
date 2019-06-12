On 3/13, I found a sample PowerShell script on hybrid-analysis.com where I tried to understand its functionality. To my knowledge, the script finds information on an infected system. The sample script that is shown on hybrid-analysis.com can be seen in Figure 1. 
```powershell$osCheckMinor = [System.Environment]::OSVersion.Version | Select -Expand Minor; $osVersion = "$osCheckMajor" + '.' + "$osCheckMinor"; $poshVersion = $PSVersionTable.PSVersion.Major;
```
Figure 1: Sample Script
	
 At this current moment in time, I am not familiar with the commands of PowerShell, however, I tested the script on a subsystem that I have available on my desktop. When the script has run, the script printed out “0” for $osCheckMinor and “"$osCheckMajor" + '.' + ” for the variable $osVersion. 
	Refer to Figure 2 to view parts of the code that was created from a random string with the variable name “`$peName” After the script generates random numbers, the code will be appended as .exe at the end of the string as seen in Figure 2. The code will then use the variable “$savePath” to the appdata folder.

Figure 2: Shows the variable name of “$peName and $savePath”
The URL https://s3.us-east-2.amazonaws.com/aiite/gfdsdfghjjhgfvbn.jpg in Figure 2 does not seem to be suspicious as it is interpreted as a regular jpg image. At a quick glance, I do not see anything suspicious about it.
