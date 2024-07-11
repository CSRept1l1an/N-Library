#Network 
## Address Resolution Protocol

### Basics
- **ARP**: Resolves IP addresses to MAC (Media Access Control) addresses on a local network.
- **Protocol**: Operates at the Link Layer (Layer 2) of the OSI model.
- **Types of ARP Messages**:
  - **ARP Request**: "Who has IP address X? Tell Y."
  - **ARP Reply**: "IP address X is at MAC address Z."

### ARP Table
- **ARP Table**: Cache storing IP-to-MAC address mappings.
- **View ARP Table**:
  - **Windows**: `arp -a`
  - **Linux/Mac**: `arp -a` or `ip neigh`

### ARP Commands
- **Display ARP Table**:
  - **Windows**: `arp -a`
  - **Linux/Mac**: `arp -a` or `ip neigh`
- **Add a Static ARP Entry**:
  - **Windows**: `arp -s <IP address> <MAC address>`
  - **Linux/Mac**: `sudo arp -s <IP address> <MAC address>`
- **Delete a Static ARP Entry**:
  - **Windows**: `arp -d <IP address>`
  - **Linux/Mac**: `sudo arp -d <IP address>`

### ARP Cache Management
- **Clear ARP Cache**:
  - **Windows**: `netsh interface ip delete arpcache`
  - **Linux**: `sudo ip -s -s neigh flush all`
  - **Mac**: `sudo arp -d -a`

### ARP Spoofing (Man-in-the-Middle Attack)
- **Concept**: An attacker sends fake ARP messages to associate their MAC address with the IP address of another device.
- **Detection**: 
  - **ARP Watch**: Monitors ARP activity on the network.
  - **Sniffing Tools**: Wireshark can capture and analyze ARP packets.
- **Protection**:
  - **Static ARP Entries**: Configure static ARP entries for critical devices.
  - **Dynamic ARP Inspection (DAI)**: Enabled on managed switches to prevent ARP spoofing.
  - **Packet Filtering**: Configure firewalls to filter suspicious ARP traffic.

### Tools
- **Wireshark**: Network protocol analyzer for capturing and analyzing ARP packets.
- **arpspoof**: Part of the dsniff suite, used for ARP spoofing.
- **arping**: Utility to discover and probe hosts on a network using ARP requests.

### Common ARP-related Issues
- **IP Address Conflicts**: Multiple devices claiming the same IP address.
- **Network Connectivity Issues**: ARP cache not updated properly, leading to stale entries.

### Example Commands
- **View ARP Table**:
```bash
  arp -a
```

- **Add Static ARP Entry**:
```bash
  arp -s 192.168.1.10 00:11:22:33:44:55
```

- **Delete ARP Entry**:
```bash
  arp -d 192.168.1.10
```

#### ARP Packet Structure
- **Hardware Type**: Type of hardware (e.g., Ethernet).
- **Protocol Type**: Type of protocol (e.g., IPv4).
- **Hardware Size**: Size of MAC address.
- **Protocol Size**: Size of IP address.
- **Opcode**: Type of ARP message (1 for request, 2 for reply).
- **Sender MAC Address**: MAC address of the sender.
- **Sender IP Address**: IP address of the sender.
- **Target MAC Address**: MAC address of the target.
- **Target IP Address**: IP address of the target.