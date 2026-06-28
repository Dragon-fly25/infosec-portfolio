# Network Credential Sniffer

**MITRE ATT&CK Mapping**  
**Tactic**: Credential Access  
**Technique**: T1040 – Network Sniffing  

**Language**: Python 3 (Scapy)

## Description

Educational tool that extracts credentials from unencrypted legacy protocols (FTP, SMTP AUTH LOGIN, and Telnet) by analyzing PCAP files.

## Features

- FTP `USER` / `PASS` extraction
- SMTP base64 AUTH LOGIN parsing
- Basic Telnet credential state tracking
- Structured logging and error handling

## Ethical Disclaimer

> **Educational Use Only**  
> This tool is intended solely for authorized testing in isolated lab environments (e.g., SANS SEC504 Windows VM). Do not use on any network without explicit permission.

## Testing Methodology (Lab Walkthrough)

### Environment
- SANS SEC504 Windows 10 Virtual Machine

### Step-by-Step Test Process

1. **Started Packet Capture in Wireshark**
   - Interface: `Adapter for loopback traffic capture`
   - Capture Filter: `port 21 or port 23 or port 25`

2. **Started Fake FTP Server**
   ```powershell
   python -m pyftpdlib -p 21 -u labuser -P LabPass123! -w

3. **Generated Traffic**
    ```powershell
   ftp 127.0.0.1
  username: labuser
  password: LabUser123!

4. Stopped capture and exported as test_ftp.pcap (Wireshark/tcpdump pcap format)

5. Ran Credential Sniffer
    ```powershell
   python credential_sniffer.py test_pcaps/test_ftp.pcap

6. Sniffer Output
[*] Starting credential sniffer on test_ftp.pcap
[*] Loaded 17 packets
[+] FTP Username: labuser | Server: 127.0.0.1
[+] FTP Password: LabPass123! | Server: 127.0.0.1
[*] Analysis completed.

## Usage 
    pip install scapy
    python credential_sniffer.py test_pcaps/test_ftp.pcap

## Learning Outcomes 
  Practical packet analysis with the Scapy library
  Understanding of credential exposure risks in legacy protocols
  Proper mapping to MITRE ATT&CK framework
  Safe lab practices for offensive security testing
  Creating documented, reproducible cybersecurity projects

## Project Status ##
  FTP extraction successfully tested
  Test PCAP included in test_pcaps/

## Future Enhancements ##
  Live sniffing mode (sniff())
  Expanded protocol support (SMTP, Telnet)
  Defensive counterpart (detection rules / log analyzer)
