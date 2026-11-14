# Computer Network Lab

Cisco Packet Tracer labs for the Computer Networks course at AIUB.

## Labs

| Lab | Topic | File |
|-----|-------|------|
| [Lab 01](lab-01/) | Two-router topology with serial link | [two-router-serial-topology.pkt](lab-01/two-router-serial-topology.pkt) |

---

## Lab 01: Two-Router Serial Topology

### Overview
Two LANs connected through two routers over a serial link. Each LAN has one switch and one PC. After configuration, all devices can reach each other using ICMP ping.

### Topology
![Topology](lab-01/images/topology.png)

```
PC0 -- Switch0 -- Router0 ==(Serial)== Router1 -- Switch1 -- PC1
```

| Device  | Model     | Connection                        |
|---------|-----------|-----------------------------------|
| PC0     | PC-PT     | Fa0 to Switch0 Fa0/1              |
| Switch0 | Switch-PT | Fa1/1 to Router0 Fa0/0            |
| Router0 | Router-PT | Se2/0 to Router1 Se2/0 (serial)   |
| Router1 | Router-PT | Fa0/0 to Switch1 Fa1/1            |
| Switch1 | Switch-PT | Fa0/1 to PC1 Fa0                  |
| PC1     | PC-PT     | Fa0 to Switch1 Fa0/1              |

### IP Addressing

| Device  | Interface | IP Address   | Subnet Mask   | Default Gateway |
|---------|-----------|--------------|---------------|-----------------|
| PC0     | Fa0       | 192.168.1.10 | 255.255.255.0 | 192.168.1.1     |
| Router0 | Fa0/0     | 192.168.1.1  | 255.255.255.0 | N/A             |
| Router0 | Se2/0     | 192.168.2.1  | 255.255.255.0 | N/A             |
| Router1 | Se2/0     | 192.168.2.2  | 255.255.255.0 | N/A             |
| Router1 | Fa0/0     | 192.168.3.1  | 255.255.255.0 | N/A             |
| PC1     | Fa0       | 192.168.3.20 | 255.255.255.0 | 192.168.3.1     |

### Networks

| Network        | Connects                          |
|----------------|-----------------------------------|
| 192.168.1.0/24 | PC0 and Router0 (LAN 1)           |
| 192.168.2.0/24 | Router0 and Router1 (serial link) |
| 192.168.3.0/24 | Router1 and PC1 (LAN 2)           |

![Device Info](lab-01/images/device-info.png)

### Routing
Static routes configured on both routers.

**Router0**
```
ip route 192.168.3.0 255.255.255.0 192.168.2.2
```

**Router1**
```
ip route 192.168.1.0 255.255.255.0 192.168.2.1
```

### Testing
ICMP ping tested between PC0, PC1, Router0 and Router1. All results: **Successful** (see the PDU list in the `.pkt` file).

### How to Open
1. Install Cisco Packet Tracer
2. Open `lab-01/two-router-serial-topology.pkt`

### Tools
- Cisco Packet Tracer

### Author
Tajmun, AIUB
