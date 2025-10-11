# 🧠 Wireshark Common Filters Cheat Sheet

A concise reference for the most commonly used **Wireshark filters**, ideal for network analysis and security testing.

---

## 🔍 Display Filters (After Capture)

| Purpose | Filter | Description |
|----------|---------|-------------|
| Show only HTTP traffic | `http` | Display only HTTP packets |
| Show only GET requests | `http.request.method == "GET"` | Display HTTP GET requests |
| Show only POST requests | `http.request.method == "POST"` | Display HTTP POST requests |
| Show only TCP packets | `tcp` | Display TCP protocol packets |
| Show only UDP packets | `udp` | Display UDP protocol packets |
| Show only DNS packets | `dns` | Display DNS queries and responses |
| Show only DNS queries | `dns.flags.response == 0` | Display only requests |
| Show only DNS responses | `dns.flags.response == 1` | Display only replies |
| Show ICMP (Ping) packets | `icmp` | Display ping requests and replies |
| Filter by IP address | `ip.addr == 192.168.1.1` | Show packets from/to a specific IP |
| Filter by source IP | `ip.src == 192.168.1.1` | Show packets from a specific source |
| Filter by destination IP | `ip.dst == 192.168.1.1` | Show packets to a specific destination |
| Filter by port | `tcp.port == 80` or `udp.port == 53` | Filter packets by port |
| Filter by destination port | `tcp.dstport == 443` | Show HTTPS packets |
| DHCP traffic | `bootp` or `dhcp` | Display DHCP packets |
| ARP packets | `arp` | Show only ARP requests/replies |
| TLS/SSL traffic | `tls` | Display HTTPS encrypted packets |
| FTP traffic | `ftp` or `ftp-data` | Show FTP data and control traffic |
| SMTP traffic | `smtp` | Show outgoing email packets |
| POP3 traffic | `pop` | Show incoming email packets |
| SSH sessions | `ssh` | Show SSH communications |
| Telnet sessions | `telnet` | Show Telnet data |
| Packets with errors | `tcp.analysis.flags` | Highlight retransmissions, dup ACKs, etc. |

---

## ⚙️ Capture Filters (Before Capture)

| Purpose | Filter | Description |
|----------|---------|-------------|
| Capture only IP packets | `ip` | Ignore non-IP traffic (e.g., ARP) |
| Capture specific host traffic | `host 192.168.1.1` | From or to a specific host |
| Capture from source only | `src host 192.168.1.1` | Capture packets from source IP |
| Capture to destination only | `dst host 192.168.1.1` | Capture packets to destination IP |
| Capture by subnet | `net 192.168.1.0/24` | Capture all packets in subnet |
| Capture by port | `port 80` | Capture only port 80 (HTTP) |
| Capture only TCP traffic | `tcp` | Capture TCP protocol packets |
| Capture only UDP traffic | `udp` | Capture UDP protocol packets |
| Capture ICMP (Ping) traffic | `icmp` | Capture ping packets |
| Capture by MAC address | `ether host aa:bb:cc:dd:ee:ff` | Filter by Ethernet (MAC) address |

---

## 🧩 Logical Operators

| Operator | Example | Description |
|-----------|----------|-------------|
| `&&` | `ip.src == 192.168.1.1 && tcp.port == 80` | AND (both conditions must match) |
| `||` | `tcp.port == 80 || tcp.port == 443` | OR (either condition matches) |
| `!` | `!arp` | NOT (exclude specific traffic) |

---

### 🧰 Notes
- Combine filters to isolate specific traffic patterns.
- Use **Display Filters** for analysis after capture.
- Use **Capture Filters** to limit data before recording.
- For deep security analysis, focus on `tcp.analysis.flags`, `tls`, and `http` filters.

---
Created by: **Cyber Security Enthusiast**
