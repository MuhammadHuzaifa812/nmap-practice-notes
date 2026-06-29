# nmap-practice-notes
Hands on cybersecurity lab demonstrating network mapping, port scanning, and reconnaissance on Metasploitable 2 using Nmap.
# Nmap Practice — Metasploitable 2

## What is Nmap?
A network scanning tool used to discover hosts, 
open ports, running services and operating systems 
on a network.

## Lab Setup
- Attacker: Kali Linux on VMware
- Target: Metasploitable 2 (local VM)
- Connection: Internal VMware network

## Commands I Practiced

### Basic Scan
nmap 192.168.x.x
- Shows open ports, their state and service names
- Fast and simple  good for first look at target

### 3 way handshake
nmap -sT 192.168.x.x
- DO three way handshake with the target using [SYN,ACK,RST]
- easily catachable

### Version Scan
nmap -sV 192.168.x.x
- Adds version numbers to each service
- Example result: vsftpd 2.3.4 on port 21

### OS Detection
nmap -O 192.168.x.x
- Guesses the operating system based on 
  how target responds to probes
- Result: Linux 2.6.x detected

### Stealth Scan
nmap -sS 192.168.x.x
- Half open TCP scan
- Doesn't complete three way handshake
- Harder to detect in logs

### Aggressive Scan
nmap -A 192.168.x.x
- Combines -sV + -O + default scripts
- Shows extra service information
- Does NOT make separate vulnerability section

### Vulnerability Script
nmap --script vuln 192.168.x.x
- Actively checks for known CVEs
- Most detailed output of all scans

## What I Learned
- Different scan types leave different traces
- -A gives more info but is louder on the network
- Always verify version numbers found by Nmap
  before attempting exploitation in Metasploit

## Important Note
All practice done on owned local lab only.
Never scan IPs you don't own it is illegal.

## Scan Results


<img width="785" height="662" alt="nmapsT" src="https://github.com/user-attachments/assets/a7bf7e86-2ae6-42f1-b114-e34e7eb5a11e" />
<img width="832" height="352" alt="nmapscript" src="https://github.com/user-attachments/assets/2fc5b7bd-798a-4f5b-a880-62c1f99e91cc" />
<img width="825" height="650" alt="nmapsS" src="https://github.com/user-attachments/assets/668a1a74-6c17-41f9-b07a-fcaf8bc7441f" />
<img width="1327" height="683" alt="nmapsV" src="https://github.com/user-attachments/assets/86cbee73-afe5-4cf6-b714-1f3a95d22090" />
<img width="905" height="532" alt="nmapA" src="https://github.com/user-attachments/assets/ea37f815-839e-4888-ae5c-7a2e0800fafd" />
<img width="1092" height="780" alt="nmapO" src="https://github.com/user-attachments/assets/0ff6f9ef-b9b8-4782-82b1-f266ab6950fe" />

