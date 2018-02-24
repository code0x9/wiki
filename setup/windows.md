## apps
* languages version manager : http://scoop.sh/
* console emulator : https://conemu.github.io/

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

## docker
### create docker-machine as usual, with more cpu, memory & storage
```
docker-machine create ^
    --virtualbox-cpu-count 4 ^
    --virtualbox-disk-size 40000 ^
    --virtualbox-memory 3072 ^
    boot2docker
```

### disable TLS
1. ssh into boot2docker
```
docker-machine ssh boot2docker
```
2. edit docker profile
```
sudo vi /var/lib/boot2docker/profile
```
3. override environment variables
```
DOCKER_HOST='-H tcp://0.0.0.0:2375'
DOCKER_TLS=no
```
4. restart boot2docker
```
docker-machine restart boot2docker
```

### setup virtualbox port forward
```
VBoxManage controlvm "boot2docker" natpf1 "docker,tcp,127.0.0.1,2375,,2375"
```

### configure tls certs on windows cmd
on 'environment variables'
```
SET DOCKER_HOST=tcp://127.0.0.1:2375
SET DOCKER_MACHINE_NAME=boot2docker
```

### configure tls certs on windows subsystem for linux
on ~/.bashrc
```
export DOCKER_HOST=tcp://127.0.0.1:2375
```