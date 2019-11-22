## Table of Contents

* [General WiFi Information](#general-wifi-information)
* [Enabling Monitor mode](#enabling-monitor-mode)
* [Attack/PenTesting](#attackpentesting)
  * [Pre-connection Attacks](#denial-of-service)
    * [MAC address changing](#MAC-address-changing)
    * [Deauthenticating All Clients From Protected WiFi Network](#wps)
    * [Deauthenticating a Client From Protected WiFi Networks](#others)
  * [Gaining Access](#encryption-attack)
    * [Find SSID of hidden networks](#wepwpawpa2)
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
  > iwconfig
  > airmon-ng check kill  
  > airmon-ng start wlan1 
  > airodump-ng wlan1mon 
    OR
  > airodump-ng --band a wlan1mon (show all type of wifi networks 5 Ghz or 2.4 Ghz)
  ```
