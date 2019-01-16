# Ethical Hacking With [Kali Linux](https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/) 

### Jubeen Shah  © 2019 

## Contents
1. Introduction
2. H/W + S/W Requirements
3. Topics
	1. Network Security
		1. Mac Address spoofing
		2. Monitoring packets


### Introduction
Add description

### Requirements 
Add description

### Topics
Add description


#### Network Security
Add description


##### Mac Address Spoofing
Add description


```shell
root@kali:~# ifconfig wlan0 down
root@kali:~# ifconfig wlan0 hw ether 00:11:22:33:44:55
root@kali:~# ifconfig wlan0 up
```

##### Monitoring packets

Add description

```shell
root@kali:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@kali:~# ifconfig wlan0 down
root@kali:~# airmon-ng check kill

Killing these processes:

  PID Name
  508 dhclient
  547 wpa_supplicant

root@kali:~# iwconfig wlan0 mode monitor
root@kali:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  Mode:Monitor  Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
root@kali:~# ifconfig wlan0 up
root@kali:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```
