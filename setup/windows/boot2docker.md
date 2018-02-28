## create docker-machine as usual, with more cpu, memory & storage
```
docker-machine create ^
    --virtualbox-cpu-count 4 ^
    --virtualbox-disk-size 40000 ^
    --virtualbox-memory 3072 ^
    boot2docker
```

## disable TLS
1. ssh into boot2docker
```
docker-machine ssh boot2docker
```
2. edit docker profile
```
sudo vi /var/lib/boot2docker/profile
```
3. override configuration
  * via environment variables
```
DOCKER_HOST='-H tcp://0.0.0.0:2375'
DOCKER_TLS=no
```
  * via /etc/docker/daemon.json : need to remove -H fd:// at /lib/systemd/system/docker.service
```
{
  "debug": false,
  "tls": false,
  "hosts": ["fd://", "tcp://0.0.0.0:2375"]
}
```
4. restart boot2docker
```
docker-machine restart boot2docker
```

## setup virtualbox port forward
```
VBoxManage controlvm "boot2docker" natpf1 "docker,tcp,127.0.0.1,2375,,2375"
```

## configure tls certs on windows cmd
on 'environment variables'
```
SET DOCKER_HOST=tcp://127.0.0.1:2375
SET DOCKER_MACHINE_NAME=boot2docker
```

## configure tls certs on windows subsystem for linux
on ~/.bashrc
```
export DOCKER_HOST=tcp://127.0.0.1:2375
```
