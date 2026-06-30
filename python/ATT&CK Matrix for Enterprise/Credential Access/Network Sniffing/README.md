# Network Credential Sniffer

### MITRE ATT&CK Mapping
* **Tactic**: Credential Access
* **Technique**: T1040 – Network Sniffing
* **Language**: Python 3 (Scapy)

---

## Description
Educational tool that extracts credentials from unencrypted legacy protocols (FTP, SMTP AUTH LOGIN, and Telnet) by analyzing PCAP files.

## Features
* **FTP** `USER` / `PASS` extraction
* **SMTP** Base64 AUTH LOGIN parsing
* **Telnet** Basic credential state tracking
* **Structured** Logging and error handling

## Ethical Disclaimer
> [!WARNING]
> **Educational Use Only**
> This tool is intended solely for authorized testing in isolated lab environments (e.g., SANS SEC504 Windows VM). Do not use on any network without explicit written permission.

---

## Testing Methodology (Lab Walkthrough)

### Environment
* SANS SEC504 Windows 10 Virtual Machine

### Step-by-Step Test Process

1. **Start packet capture in Wireshark**
   * **Interface**: `Adapter for loopback traffic capture`
   * **Capture Filter**: `port 21 or port 23 or port 25`

2. **Start fake FTP server**
   ```powershell
   python -m pyftpdlib -p 21 -u labuser -p labpass123! -w
   ```

3. **Generate traffic**
   ```powershell
   ftp 127.0.0.1
   # Username: labuser
   # Password: labuser123!
   ```

4. **Stop capture**
   * Export file as `test_ftp.pcap` (Wireshark/tcpdump PCAP format).

5. **Run credential sniffer**
   ```powershell
   python credential_sniffer.py test_pcaps/test_ftp.pcap
   ```

6. **Sniffer output**
   ```text
   [*] Starting credential sniffer on test_ftp.pcap
   [*] Loaded 17 packets
   [+] FTP Username: labuser | Server: 127.0.0.1
   [+] FTP Password: labpass123! | Server: 127.0.0.1
   [*] Analysis completed.
   ```

---

## Usage

### Installation
```bash
pip install scapy
```

### Execution
```bash
python credential_sniffer.py test_pcaps/test_ftp.pcap
```

---

## Learning Outcomes
* **Practical Packet Analysis**: Gained hands-on experience using the Scapy library.
* **Protocol Security**: Developed a deep understanding of credential exposure risks in legacy protocols.
* **Framework Alignment**: Mastered proper mapping of security concepts to the MITRE ATT&CK framework.
* **Defensive Mindset**: Practiced safe lab habits for offensive security testing and creating documented, reproducible cybersecurity projects.

## Future Enhancements
* **Live sniffing mode 
* **Expanded protocol support (SMTP. Telnet)
* **Defensive counterpart (detection rules / log analyzer)
