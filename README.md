# fake-data

## Getting Started
### Enable your Internet Connection in CentOS 7 using VirtualBox
- Article: https://emcorrales.com/blog/how-to-enable-internet-access-on-centos7-virtualbox
- Video: https://youtu.be/PlfxwKHY82M

Quick Steps:
1. In Terminal, edit your network interface configuration
```
sudo vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
```
2. Change to `ONBOOT=yes`, don't forget to SAVE. In vim, `ESC` to enter command mode, `:wq` to save and exit.
3. Restart network to apply changes
```
sudo systemctl restart network.service
```


## `http.log`
- http.log - `bit.ly/httplog`
- To download: `curl -L -o http.log bit.ly/httplog`

## `sample.log`
- sample.log - `bit.ly/samplelogfile`
- To download: `curl -L -o sample.log bit.ly/samplelogfile`

## `star_wars.txt`
- star_wars.txt - `bit.ly/starwarstxt`
- To download: `curl -L -o star_wars.txt bit.ly/starwarstxt`

## `regex.txt`
- regex.txt - `bit.ly/regextxt`
- To download: `curl -L -o regex.txt bit.ly/regextxt`

