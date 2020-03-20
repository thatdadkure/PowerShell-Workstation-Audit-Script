# PowerShell-Workstation-Audit

A simple PowerShell script which can be copied/pasted into a PowerShell console window and retrieve auditable workstation configuration settings. This script only runs a series a queries (it does not make any modifications) and then creates a text document on the user's desktop named after the computer name which can then be uploaded to your favorite auditor :)

This script may need to be run on each workstaiton being audited seperately.

systeminfo | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt" ; wmic qfe list | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt" -append ; wmic product get name,version | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt" -append ; manage-bde -status | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt" -append ; net share | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt" -append ; wmic /Node:localhost /Namespace:\\root\SecurityCenter2 Path AntiVirusProduct Get * /value | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt" -append ; netsh advfirewall show allprofiles | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt"-append ; get-item 'HKCU:\Software\Policies\Microsoft\Internet Explorer\Main' | Out-File "$($env:USERPROFILE)\Desktop\$env:computername.txt"-append
