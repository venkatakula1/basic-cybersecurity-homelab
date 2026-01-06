BASIC CYBERSECURITY HOMELAB

Network Scanning and Traffic Analysis with Nmap and Wireshark

PROJECT OVERVIEW 
-> This project demonstrates a basic offensive and defensive cybersecurity workflow.
-> I have used two virtual machines: A Kali Linux attacker machine which performs network scans using Nmap against an Ubuntu victim machine.
-> While the Ubuntu system captures network traffic using Wireshark.

My goal is to understand how network scans work and how they appear at the packet level.

ARCHITECTURE
Linux Mint host → VirtualBox → Kali VM (attacker, 192.168.56.x) and Ubuntu VM (victim, 192.168.56.x).​

OBJECTIVES
-> Configure an isolated virtual network using VirtualBox.

-> Perform network reconnaissance using Nmap on Kali.

-> Capture and analyse packets using wireshark on Ubuntu.

-> Identify how TCP SYN scans appear in the network traffic.


TOOLS AND WHY USED
-> VirtualBox: isolate lab safely.

-> Kali: attacker box with security tools.

-> Ubuntu: victim system.

-> Nmap: discover open ports and services for reconnaissance.

​-> Wireshark: inspect traffic and understand how scans look on the wire.

IMPORTANT
-> In VirtualBox Adapter 1 should be NAT(Network Address Translation), turn on Adapter 2 and set it to Host-only network(vboxnet0)

-> Verify connectivity by using "ping <eachothers ip address>" on both VM's terminals (use "ip a" for the ip address).

-> Kali usually comes with Nmap pre-installed, Download Wireshark on Ubuntu victim machine.

CAPTURE TRAFFIC(ubuntu) 
-> Launch Wireshark

-> Start capturing after you select an interface.

PERFORM SCANS(kali)
-> nmap <ubuntu_ip>

-> sudo nmap -sS <ubuntu_ip>

WIRESHARK FILTERS USED
-> ip.addr == <kali_ip>

-> tcp.flags.syn == 1 && tcp.flags.ack == 0

OBSERVATIONS
-> Multiple TCP SYN packets sent to different ports.

-> Open ports respond with SYN-ACK.

-> Closed ports respond with RST.

-> Observed the full TCP three‑way handshake (SYN, SYN‑ACK, ACK) on open ports and only SYN/RST on closed ports.



WHAT I LEARNED

-> Difference between open/closed/filtered ports.

-> How Nmap performs network reconnaissance.

-> Why defenders monitor for repeated SYNs from one host to many ports.

-> How active scans appear in packet level network traffic.

-> Basics of detecting reconnaissance activity.



##
Venkat Akula
MS in CS | Cybersecurity interest
