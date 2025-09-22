# Task 1 — Local Network Port Scan

## Objective
Perform a TCP SYN scan on the local network to identify open ports and assess security risks.

## Tools Used
- **Nmap** (via Zenmap GUI)
- **Wireshark** (for packet capture and verification)

## Scan Command
```bash
nmap -sS 192.168.0.0/24
```

## Results
### Host 1: 192.168.0.1 (Router — D-Link)
- 53/tcp open (DNS)
- 80/tcp open (HTTP - admin panel)

### Host 2: 192.168.0.100
- All scanned ports closed

### Host 3: 192.168.0.103 (Windows Device / VM)
- 135/tcp open (MS RPC)
- 139/tcp open (NetBIOS-SSN)
- 445/tcp open (SMB)
- 902/tcp open (VMware related)
- 912/tcp open (Apex-mesh service)
- 2869/tcp open (ICS LAP — UPnP)
- 8090/tcp open (Ops messaging)

## Risk Analysis
- **Router (192.168.0.1):**
  - HTTP on port 80 is unencrypted → susceptible to credential theft.
- **Windows host (192.168.0.103):**
  - Ports 135/139/445 are known SMB vulnerabilities.
  - Additional services increase attack surface.
- **Device 192.168.0.100:** Secure (no open ports).

## Recommendations
- Switch router management to HTTPS and restrict admin access.
- Disable SMB/NetBIOS if not required.
- Keep all systems patched and firewall-enabled.
- Close unused ports (902, 912, 8090).
- Regularly monitor with Nmap + Wireshark.

## Screenshots
- Included in `screenshots/` folder:
  - Nmap results from Zenmap
  - Host/Ports view
  - Raw Nmap output

## Outcome
Gained practical experience in:
- Port scanning with Nmap
- Identifying open ports & services
- Assessing risks and recommending mitigations

