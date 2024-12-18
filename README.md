TP-Link VN020 DHCP Memory Corruption (CVE-2024-11237)
Critical Vulnerability in DHCP Packet Processing
Overview
A critical vulnerability has been discovered in TP-Link VN020 F3v(T) routers running firmware version TT_V6.2.1021. The vulnerability allows remote attackers to trigger a stack-based buffer overflow through specially crafted DHCP DISCOVER packets, leading to denial of service (DoS) conditions.

Affected Devices:

Router Model: TP-Link VN020-F3v(T)
Firmware Version: TT_V6.2.1021
Deployment: Primarily through Tunisie Telecom and Topnet ISPs
Confirmed Variants: Also affects Algerian and Moroccan versions
Important Note: Due to the proprietary nature of the firmware, the exact internal implementation details are unknown. This analysis is based on observed behavior and black-box testing.

Vulnerability Details
CVE ID: CVE-2024-11237
Type: Stack-based Buffer Overflow (CWE-121)
Attack Vector: Remote (DHCP DISCOVER Packet)
Authentication: None Required
Port: UDP/67 (DHCP Server)
Impact: DoS (Confirmed) & RCE (Possible)
Complexity: Low



Normal DHCP Hostname Processing

Stack Layout (Normal Case)

+------------------------+ Higher addresses
|     Previous Frame     |
+------------------------+
|   Return Address (4)   |
+------------------------+
|    Saved EBP (4)       |
+------------------------+
|                        |
|   Hostname Buffer      |
|      (64 bytes)        |
|                        |
+------------------------+ Lower addresses
|    Other Variables     |
+------------------------+
