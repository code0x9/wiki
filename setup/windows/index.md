## apps
* languages version manager : http://scoop.sh/
* console emulator : https://conemu.github.io/
* docker: [docker install guide](boot2docker.md)

## scoop
* packages
  * Gow - The lightweight alternative to Cygwin : https://github.com/bmatzelle/gow
  * gitkraken
  * go
  * nodejs
  * python

## conemu
* reuse current director on ConEmu
  * put task parameter ```/dir "%CD%"``` on {Shells::cmd} task. see https://chrisseroka.wordpress.com/2017/03/30/cmderconemu-starting-new-tab-in-current-folder/

## powershell
* profile paths

| Description | Path |
| ------------ | ------ |
| Current User, Current Host - console | $Home\[My ]Documents\WindowsPowerShell\Profile.ps1 |
| Current User, All Hosts | $Home\[My ]Documents\Profile.ps1 |
| All Users, Current Host - console | $PsHome\Microsoft.PowerShell_profile.ps1 |
| All Users, All Hosts | $PsHome\Profile.ps1 |
| Current user, Current Host - ISE | $Home\[My ]Documents\WindowsPowerShell\Microsoft.P owerShellISE_profile.ps1 |
| All users, Current Host - ISE | $PsHome\Microsoft.PowerShellISE_profile.ps1 |

* create initial powershell profile

```
New-Item $profile -Type File -Force
```

https://blogs.technet.microsoft.com/heyscriptingguy/2012/05/21/understanding-the-six-powershell-profiles/

* allow old ssl on powershell

```
[Net.ServicePointManager]::SecurityProtocol = 
  [Net.SecurityProtocolType]::Tls12 -bor `
  [Net.SecurityProtocolType]::Tls11 -bor `
  [Net.SecurityProtocolType]::Tls
```
