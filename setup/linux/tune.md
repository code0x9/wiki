## speed up slow network
* disable ipv6
```
sudo su
echo "#disable ipv6" >> /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" >> /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" >> /etc/sysctl.conf
```
* Debian Avahi-daemon bugfix
  * in /etc/nsswitch.conf, replace
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
into
```
hosts:          files dns
```

* https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/

## fix semicolon input delay on fcitx
* disable addon -> quickphrase
