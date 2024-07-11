#Network 
## OSPF (Open Shortest Path First)

### Basics
- **OSPF**: A link-state routing protocol used within an Autonomous System (AS).
- **Protocol**: Operates at the Internet Layer (Layer 3) of the OSI model.
- **RFC**: Defined in RFC 2328.
- **Algorithm**: Uses Dijkstra's Shortest Path First (SPF) algorithm.

### Key Concepts
- **Areas**: OSPF networks are divided into areas to optimize traffic.
  - **Backbone Area (Area 0)**: Central area to which all other areas must connect.
  - **Stub Area**: Reduces routing information.
  - **Totally Stubby Area**: Further restricts routing information.
  - **Not-So-Stubby Area (NSSA)**: Allows for limited external routes.
- **Router Types**:
  - **Internal Router**: All interfaces within the same area.
  - **Backbone Router**: At least one interface in Area 0.
  - **Area Border Router (ABR)**: Connects two or more areas.
  - **Autonomous System Boundary Router (ASBR)**: Connects to external networks.
- **LSA Types**:
  - **Type 1**: Router LSA
  - **Type 2**: Network LSA
  - **Type 3**: Summary LSA
  - **Type 4**: ASBR Summary LSA
  - **Type 5**: AS External LSA
  - **Type 7**: NSSA LSA

### OSPF Packet Types
- **Hello**: Establishes and maintains neighbor relationships.
- **Database Description (DBD)**: Summarizes the database contents.
- **Link-State Request (LSR)**: Requests specific LSAs from a neighbor.
- **Link-State Update (LSU)**: Contains the LSAs.
- **Link-State Acknowledgment (LSAck)**: Acknowledges receipt of LSAs.

### OSPF States
1. **Down**
2. **Init**
3. **Two-Way**
4. **ExStart**
5. **Exchange**
6. **Loading**
7. **Full**

### OSPF Metrics
- **Cost**: The OSPF metric is based on the interface bandwidth. The formula is:
  ``` Cost = Reference Bandwidth / Interface Bandwidth ```
  - **Reference Bandwidth**: Typically 100 Mbps (can be changed).

### Basic Configuration (Cisco IOS)
1. **Enable OSPF**:
```bash
router ospf 1
```
1. **Configure Router ID**:
```bash
router-id <Router-ID>
```
1. **Advertise Networks**:
```bash
network <IP-Address> <Wildcard-Mask> area <Area-ID>
```
1. **Set OSPF Cost**:
```bash
interface <Interface-Name>
ip ospf cost <Cost>
```

#### Example Configuration
```bash
router ospf 1
 router-id 1.1.1.1
 network 192.168.1.0 0.0.0.255 area 0
 network 192.168.2.0 0.0.0.255 area 1
```

### OSPF Neighbor Relationships
- **Neighbor Requirements**:
  - Same Area ID
  - Same Subnet
  - Same Hello and Dead Intervals
  - Same Authentication (if used)
- **Verify Neighbors**:
```bash
show ip ospf neighbor
```

### OSPF Network Types
- **Broadcast**: Uses DR/BDR elections (e.g., Ethernet).
- **Non-Broadcast**: No DR/BDR elections; requires manual neighbor configuration (e.g., Frame Relay).
- **Point-to-Point**: No DR/BDR elections; directly connected routers (e.g., Serial links).
- **Point-to-Multipoint**: No DR/BDR elections; multiple routers connected (e.g., hub-and-spoke).

### OSPF Timers
- **Hello Interval**: How often Hello packets are sent (default 10 seconds).
- **Dead Interval**: Time without Hello packets before neighbor is declared dead (default 40 seconds).

#### Troubleshooting Commands
- **OSPF Status**:
```bash
show ip ospf
```
- **OSPF Interfaces**:
```bash
show ip ospf interface
```
- **OSPF Neighbors**:
```bash
show ip ospf neighbor
```
- **OSPF Database**:
```bash
show ip ospf database
```

#### Advanced Configuration
- **Stub Areas**:
```bash
area <Area-ID> stub
```
- **Totally Stubby Areas**:
```bash
area <Area-ID> stub no-summary
```
- **NSSA Areas**:
```bash
area <Area-ID> nssa
```

This cheat sheet provides a comprehensive overview of OSPF, covering key concepts, commands, and configurations. Let me know if you need more details or specific examples!