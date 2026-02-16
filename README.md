# Branch Office Network - Cisco Packet Tracer Simulation

Developed as part of my Networking Portfolio, this repository contains a network simulation for a branch office environment designed in **Cisco Packet Tracer**. The project focuses on core networking concepts, including DHCP services, IPv4/IPv6 dual-stack connectivity, and essential device hardening.

## 🚀 Key Features & Technologies

* **Dual-Stack Routing (IPv4 & IPv6):** Implementation of both address families to ensure modern connectivity.
* **DHCP Server Configuration:** The `Office-Router` acts as the DHCP server for the local network (Pool: "office"), providing automated addressing to end devices.
* **Network Hardening & Security:**
    * **Management Security:** Encrypted passwords (`service password-encryption`) and a secret enable password.
    * **Remote Access:** SSH is configured for secure remote management, disabling insecure Telnet.
    * **Port Security:** All unused FastEthernet and Gigabit ports on the switch have been administratively disabled (`shutdown`) to prevent unauthorized physical access.
    * **Banner MOTD:** Legal warning banner configured to discourage unauthorized access.
    * **DNS Server:** A customized DNS Server to enable SSH, provide more speed to the network, and more granular security. 

## 📊 Addressing Table

| Device | Interface | IPv4 Address | IPv6 Address | Description |
| :--- | :--- | :--- | :--- | :--- |
| **Office-Router** | G0/0 | DHCP (Internet) | 2000:DB8:ACAD:A::1/64 | WAN Interface |
| **Office-Router** | G0/1 | 192.168.1.1/24 | 2000:DB8:ACAD:B::1/64 | LAN Gateway |
| **Office-Router** | Lo0 | 10.255.255.1/32 | N/A | Loopback Interface |
| **Office-Switch** | VLAN 1 | 192.168.1.254/24 | N/A | Management IP |

## 🛠️ Configuration Highlights

### DHCP Exclusions
To prevent IP conflicts with static devices (like the Switch and the Gateway), the following addresses are excluded from the DHCP pool:
* `192.168.1.1` (Router)
* `192.168.1.100` (Reserved)

### Security Practices
The switch configuration shows a proactive security stance by shutting down ports `Fa0/3` through `Fa0/22`. This ensures that "plug-and-play" attacks are mitigated within the office.

## 📂 Repository Structure

* `configs/`: Raw `.txt` files containing the `show running-config` output for the Router and Switch.
* `img/`: Screenshots of the topology and successful connectivity tests (Pings/Web Browser).
* 
