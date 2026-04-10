# Shadow-Trace

## Objective
Perform static malware analysis on `windows-update.exe` and correlate
findings with two EDR alerts involving Base64 and CharCode obfuscation.

### Skills Learned
- PE binary static analysis (architecture, SHA-256, strings, imports)
- Hardcoded C2 URL and domain IOC extraction from binary strings
- WS2_32.dll import identification (network capability)
- Base64 decoding of obfuscated PowerShell command (EDR alert 1)
- Decimal CharCode decoding of obfuscated browser download (EDR alert 2)
- Filename extraction from JavaScript download command
- Multi-source evidence correlation (static analysis + EDR alerts)

### Tools Used
- pestudio — PE static analysis
- CyberChef — From Base64, From Decimal
- sigcheck.exe, strings.exe (Sysinternals)
- HxD (hex editor)
- EDR agent (simulated)

## Steps
`windows-update.exe` loaded in pestudio → architecture: 64-bit, SHA-256 hash
extracted. Strings section revealed C2 URL and domain `responses.tryhatme[.]com`.
Base64 string decoded via CyberChef → hidden flag. WS2_32.dll import confirmed
network capability. EDR Alert 1 (powershell.exe): Base64 payload decoded →
`hxxps://tryhatme[.]com/dev/main[.]exe`. EDR Alert 2 (chrome.exe): decimal
CharCode array decoded → `hxxps://reallysecureupdate.tryhatme[.]com/update[.]exe`,
filename: `test.txt`.

*Ref 1: pestudio strings — C2 URL and Base64 flag decoded via CyberChef*
*Ref 2: EDR Alert 2 — CyberChef From Decimal revealing hidden download URL*
