# TryHackMe — Pre-Security: Networking Fundamentals

**Date:** June 8, 2026
**Path:** Pre-Security — in progress
**Status:** 🔄 In progress

---

## LAN Topologies

| Topology | How it works | Pros | Cons |
|----------|-------------|------|------|
| Star | All devices connect to central switch/hub | Reliable, scalable | Expensive, central device = single point of failure |
| Bus | All devices on one backbone cable | Cheap, easy to set up | Bottlenecks easily, hard to troubleshoot, no redundancy |
| Ring | Devices connected in a loop | Less cabling, easy to troubleshoot direction | Slow, one break = entire network down |

## Switch vs Router
| Device | Purpose |
|--------|---------|
| Switch | Connects devices within same network, sends data only to intended port |
| Router | Connects different networks, finds best path for data to travel |

Switches and routers can connect to each other for **redundancy** —
if one path fails, data takes another route.

---

## Subnetting
Splitting a network into smaller networks within itself.

| Address Type | Purpose | Example |
|-------------|---------|---------|
| Network Address | Identifies the network | 192.168.1.0 |
| Host Address | Identifies a device on the subnet | 192.168.1.100 |
| Default Gateway | Sends data to other networks | 192.168.1.254 |

**Real world example:**
A café has two subnets:
- One for staff and cash registers
- One for public WiFi hotspot

Subnetting keeps them separated and secure.

---

## ARP (Address Resolution Protocol)
Maps IP addresses to MAC addresses on a network.

**How it works:**
1. Device broadcasts **ARP Request** — "Who has this IP address?"
2. Device with that IP replies with **ARP Reply** — "I do, here's my MAC"
3. Requesting device stores the mapping in its **ARP cache**

---

## OSI Model — 7 Layers

| Layer | Name | What happens |
|-------|------|-------------|
| 7 | Application | User interaction — HTTP, FTP, DNS |
| 6 | Presentation | Encryption, formatting, compression |
| 5 | Session | Opens and manages sessions |
| 4 | Transport | TCP/UDP — reliable or fast delivery |
| 3 | Network | IP addressing and routing |
| 2 | Data Link | MAC addresses, frames, switches |
| 1 | Physical | Cables, signals, raw bits |

**Memory trick:** All People Seem To Need Data Processing (bottom to top)

---

## Packets vs Frames
- **Packet** — Layer 3 (Network) — contains IP addresses
- **Frame** — Layer 2 (Data Link) — wraps the packet, contains MAC addresses
- Think of it as: Frame = envelope, Packet = letter inside

### IP Packet Headers
| Header | Purpose |
|--------|---------|
| Time to Live (TTL) | Stops packet looping forever on network |
| Checksum | Checks data integrity |
| Source Address | Where packet came from |
| Destination Address | Where packet is going |

---

## TCP vs UDP

| | TCP | UDP |
|-|-----|-----|
| Connection | Connection-based | Connectionless/stateless |
| Reliability | Guaranteed delivery | No guarantee |
| Speed | Slower | Much faster |
| Error checking | Yes | No |
| Use case | File transfer, web, email | Video streaming, voice chat, gaming |

---

## TCP Three-Way Handshake
Process to establish a connection before sending data.

| Step | Message | Who sends it | Purpose |
|------|---------|-------------|---------|
| 1 | SYN | Client | Initiate connection |
| 2 | SYN/ACK | Server | Acknowledge + sync back |
| 3 | ACK | Client | Confirm connection established |
| 4 | DATA | Both | Actual data transfer |
| 5 | FIN | Either | Close connection cleanly |
| — | RST | Either | Abort connection immediately |

**Closing a connection:**
Device sends FIN → other device sends FIN/ACK → connection closed.

---

## TCP/IP Model — 4 Layers
Simplified version of OSI model:
1. Application
2. Transport
3. Internet
4. Network Interface

---

## UDP Packet Headers
Simpler than TCP — fewer headers:

| Header | Purpose |
|--------|---------|
| TTL | Stops packet looping |
| Source Address | Where packet came from |
| Destination Address | Where packet is going |
| Source Port | Randomly chosen port sender uses |
| Destination Port | Port of service on receiving device |
| Data | The actual content being sent |

---

## Key Takeaways
- Star topology is most common — scalable but expensive
- Switches send data to specific ports, hubs broadcast to all
- Subnetting improves security by isolating network segments
- ARP maps IP to MAC address using broadcast requests
- OSI has 7 layers, TCP/IP has 4 — both describe same process
- TCP = reliable but slow, UDP = fast but no guarantee
- Three-way handshake = SYN → SYN/ACK → ACK
- Packets are Layer 3, Frames are Layer 2
