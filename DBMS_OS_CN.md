# DBMS — MCQ Cheatsheet (2 Din Mein Set)

---

## 1. Keys

| Key | Definition |
|---|---|
| Primary Key | Unique + Not Null |
| Foreign Key | Dusri table ka Primary Key |
| Candidate Key | Jo primary key ban sakti hai |
| Super Key | Candidate key + extra attributes |
| Composite Key | 2+ columns milke unique |
| Surrogate Key | Artificial key (auto-increment) |

**Trick:** Candidate ⊂ Super Key. Primary Key = Best Candidate Key.

---

## 2. Normalization — Sabse Zyada Poochha Jaata Hai

| Form | Rule |
|---|---|
| 1NF | No repeating groups, atomic values |
| 2NF | 1NF + No partial dependency (composite key pe) |
| 3NF | 2NF + No transitive dependency |
| BCNF | 3NF + Every determinant is candidate key |

**Trick to remember:** **"Atomically, Partially, Transitively, Bcnf-ly"**

**Partial dependency** = Non-key attribute depends on **part** of composite key

**Transitive dependency** = A→B→C (C depends on A through B)

---

## 3. ACID Properties

| Property | Meaning |
|---|---|
| Atomicity | All or nothing |
| Consistency | DB valid state pe rahe |
| Isolation | Transactions ek dusre ko affect na karein |
| Durability | Committed data permanent rahe |

---

## 4. Joins — Diagram Yaad Rakho

```
INNER JOIN  → Common rows only
LEFT JOIN   → Left table sab + common
RIGHT JOIN  → Right table sab + common
FULL JOIN   → Dono tables sab rows
CROSS JOIN  → Cartesian product (m×n rows)
SELF JOIN   → Same table se join
```

**Trick:** LEFT JOIN mein right side NULL aa sakta hai unmatched rows mein.

---

## 5. Transactions — States

```
Active → Partially Committed → Committed
                ↓
             Failed → Aborted
```

---

## 6. Concurrency Problems

| Problem | Explanation |
|---|---|
| Dirty Read | Uncommitted data read kiya |
| Non-repeatable Read | Same query, alag result |
| Phantom Read | New rows appear ho gayi |
| Lost Update | Ek transaction ka update overwrite ho gaya |

**Isolation levels yaad rakho:**
```
Read Uncommitted → Read Committed → Repeatable Read → Serializable
(Dirty Read ✓)    (Dirty Read ✗)   (Non-repeat ✗)   (Phantom ✗)
```

---

## 7. Indexing

| Type | Use |
|---|---|
| Primary Index | Ordered, on primary key |
| Secondary Index | Unordered data pe |
| Clustered | Data physically sorted (1 per table) |
| Non-Clustered | Separate structure, pointer to data |
| B+ Tree Index | Most common in DBMS |

**Trick:** Clustered index = data aur index saath. Non-clustered = alag.

---

## 8. SQL Execution Order

```
FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

**Trick:** **F-J-W-G-H-S-O-L** → "From Join Where Group Having Select Order Limit"

---

## 9. SQL Important Concepts

```sql
-- WHERE vs HAVING
WHERE  → GROUP BY se pehle filter (rows pe)
HAVING → GROUP BY ke baad filter (groups pe)

-- DELETE vs TRUNCATE vs DROP
DELETE   → Rows delete, rollback possible, WHERE use ho sakta
TRUNCATE → Sab rows delete, rollback nahi, fast
DROP     → Table hi delete

-- UNION vs UNION ALL
UNION     → Duplicates remove karta hai
UNION ALL → Duplicates rakhta hai (fast)
```

---

## 10. ER Diagram

| Symbol | Meaning |
|---|---|
| Rectangle | Entity |
| Ellipse | Attribute |
| Diamond | Relationship |
| Double Ellipse | Multivalued attribute |
| Dashed Ellipse | Derived attribute |

**Cardinality:**
- 1:1 → Ek se ek
- 1:N → Ek se many
- M:N → Many to many (junction table chahiye)

---

## 11. Deadlock

**Conditions (Coffman's — sab 4 saath honein):**
1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

**Prevention:** Circular Wait tod do → resources ko order mein allocate karo.

---

## 12. Most Asked MCQ Facts

- Default join = **INNER JOIN**
- NULL = NULL is **FALSE** (NULL = NULL nahi hota)
- `IS NULL` use karo, `= NULL` nahi
- Primary key = Unique + Not Null automatically
- Foreign key can be **NULL**
- **VIEW** = Virtual table, data store nahi hota
- **TRIGGER** = Automatic action on INSERT/UPDATE/DELETE
- **Stored Procedure** = Precompiled SQL block
- **Cursor** = Row by row processing
- B+ Tree → Leaf nodes linked list ki tarah connected hote hain

---

## 13. CAP Theorem

```
Consistency + Availability + Partition Tolerance
— Teeno ek saath possible nahi
```

- **CA** → Traditional RDBMS (MySQL)
- **CP** → MongoDB, HBase
- **AP** → Cassandra, CouchDB

---

OS deta hoon next?










# OS — MCQ Cheatsheet (2 Din Mein Set)

---

## 1. Process vs Thread

| | Process | Thread |
|---|---|---|
| Memory | Alag address space | Shared memory |
| Communication | IPC chahiye | Direct |
| Overhead | Zyada | Kam |
| Crash effect | Sirf wo process | Poora process crash |

**Trick:** Thread = lightweight process. Same process ke threads memory share karte hain.

---

## 2. Process States

```
New → Ready → Running → Terminated
                ↓↑
              Waiting
```

- **Ready → Running** = Dispatch
- **Running → Waiting** = I/O request
- **Running → Ready** = Preemption (time slice khatam)

---

## 3. CPU Scheduling Algorithms

| Algorithm | Type | Key Point |
|---|---|---|
| FCFS | Non-preemptive | Convoy effect problem |
| SJF | Non-preemptive | Minimum avg waiting time |
| SRTF | Preemptive | SJF ka preemptive version |
| Round Robin | Preemptive | Time quantum fixed |
| Priority | Both | Starvation possible |
| MLQS | Preemptive | Multiple queues, fixed priority |

**Trick:**
- **Convoy Effect** = FCFS mein bada process sab ko rokta hai
- **Starvation** = Priority mein chhote process kabhi execute nahi hote
- **Aging** = Starvation solution — priority badhate jao time ke saath

---

## 4. Scheduling Formulas — Poochhe Jaate Hain

```
Turnaround Time = Completion Time - Arrival Time
Waiting Time    = Turnaround Time - Burst Time
Response Time   = First CPU Time - Arrival Time
```

---

## 5. Deadlock — Same as DBMS

**Coffman's 4 Conditions:**
1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

**Detection:** Resource Allocation Graph (RAG)
- Cycle hai + single instance = Deadlock
- Cycle hai + multiple instance = Maybe deadlock

**Recovery:**
- Process terminate karo
- Resource preempt karo

---

## 6. Memory Management

| Concept | Key Point |
|---|---|
| Paging | Fixed size blocks (pages/frames) |
| Segmentation | Variable size blocks (logical) |
| Virtual Memory | RAM se bada memory illusion |
| Page Fault | Page RAM mein nahi, disk se laana padega |
| Thrashing | Itne page faults ki CPU kaam nahi kar pata |

**Trick:**
- Page size power of 2 hoti hai
- Internal Fragmentation → Paging mein
- External Fragmentation → Segmentation mein

---

## 7. Page Replacement Algorithms

| Algorithm | Key Point |
|---|---|
| FIFO | Oldest page replace karo |
| LRU | Least Recently Used replace karo |
| Optimal | Future mein sabse door wala replace karo (theoretical) |
| LFU | Least Frequently Used |

**Trick:**
- **Belady's Anomaly** = FIFO mein frames badhane se page faults badh jaate hain
- LRU mein Belady's Anomaly nahi hoti
- Optimal = Best performance but practical nahi

---

## 8. Page Table

```
Logical Address  = Page Number + Offset
Physical Address = Frame Number + Offset

Page Table size  = 2^(page number bits)
```

**TLB** = Translation Lookaside Buffer = Page table cache (fast lookup)

**Effective Access Time:**

```
EAT = Hit ratio × TLB time + (1 - Hit ratio) × (TLB + Memory time)
```

---

## 9. Inter Process Communication (IPC)

| Method | Key Point |
|---|---|
| Pipe | Unidirectional, related processes |
| Named Pipe | Unrelated processes bhi |
| Message Queue | Asynchronous |
| Shared Memory | Fastest IPC |
| Semaphore | Synchronization ke liye |
| Socket | Network communication |

**Trick:** Shared Memory = Fastest. Socket = Network ke liye.

---

## 10. Semaphore

```
wait(S)  / P(S) → S-- (acquire)
signal(S)/ V(S) → S++ (release)

Binary Semaphore  = 0 or 1 (mutex jaisa)
Counting Semaphore = Any value
```

**Classic Problems:**
- Producer-Consumer → Semaphore use
- Reader-Writer → Multiple readers ok, writer exclusive
- Dining Philosophers → Deadlock example

---

## 11. File System

| Allocation | Key Point |
|---|---|
| Contiguous | Fast access, external fragmentation |
| Linked | No fragmentation, slow random access |
| Indexed | Index block, fast random access |

**Inode** = File metadata store karta hai (name nahi, sirf permissions/size/pointers)

---

## 12. Disk Scheduling

| Algorithm | Key Point |
|---|---|
| FCFS | Request order mein |
| SSTF | Nearest seek first (starvation possible) |
| SCAN | Elevator — ek direction mein jao, wapas aao |
| C-SCAN | Circular — sirf ek direction |
| LOOK | SCAN but end tak nahi jaata |

**Trick:** SSTF = Best avg seek time but starvation. SCAN = Elevator algorithm.

---

## 13. Most Asked MCQ Facts

- **Kernel** = OS ka core, hardware directly manage karta hai
- **System Call** = User program ka OS se request
- **Context Switch** = CPU ek process se dusre pe switch karna
- **Spooling** = Slow device ke liye buffer (printer)
- **Multiprogramming** = Multiple programs RAM mein
- **Multitasking** = Rapid switching between processes
- **Multiprocessing** = Multiple CPUs
- **Multithreading** = Multiple threads in one process
- **Fork()** = New child process create karta hai
- **Zombie Process** = Execute ho gaya but parent ne wait() nahi kiya
- **Orphan Process** = Parent mar gaya, child chal raha hai (init adopt karta hai)
- **Critical Section** = Shared resource access karne wala code block
- **Mutex** = Binary lock, owner hi unlock kar sakta hai
- **Semaphore** = Counter based, koi bhi signal kar sakta hai

---

CN deta hoon next?












# CN — MCQ Cheatsheet (2 Din Mein Set)

---

## 1. OSI Model — Sabse Zyada Poochha Jaata Hai

| Layer | Number | Key Protocol | Device |
|---|---|---|---|
| Physical | 1 | Ethernet, USB | Hub, Repeater |
| Data Link | 2 | MAC, ARP | Switch, Bridge |
| Network | 3 | IP, ICMP, OSPF | Router |
| Transport | 4 | TCP, UDP | — |
| Session | 5 | NetBIOS, PPTP | — |
| Presentation | 6 | SSL, TLS, JPEG | — |
| Application | 7 | HTTP, FTP, DNS, SMTP | — |

**Trick to remember:** **"Please Do Not Throw Sausage Pizza Away"** (Bottom to Top)

---

## 2. TCP vs IP Model

| OSI | TCP/IP |
|---|---|
| Application + Presentation + Session | Application |
| Transport | Transport |
| Network | Internet |
| Data Link + Physical | Network Access |

---

## 3. TCP vs UDP

| | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable | Unreliable |
| Speed | Slow | Fast |
| Order | Guaranteed | Not guaranteed |
| Use | HTTP, FTP, Email | DNS, Video, Gaming |
| Header size | 20 bytes | 8 bytes |

**Trick:** TCP = Phone call. UDP = Letter post.

---

## 4. IP Addressing

**IPv4** = 32 bits = 4 octets (192.168.1.1)
**IPv6** = 128 bits = 8 groups of 4 hex

**Classes:**

| Class | Range | Default Subnet | Use |
|---|---|---|---|
| A | 1–126 | 255.0.0.0 /8 | Large networks |
| B | 128–191 | 255.255.0.0 /16 | Medium networks |
| C | 192–223 | 255.255.255.0 /24 | Small networks |
| D | 224–239 | — | Multicast |
| E | 240–255 | — | Research |

**Special IPs:**
- 127.0.0.1 = Loopback (localhost)
- 0.0.0.0 = Default route
- 255.255.255.255 = Broadcast

---

## 5. Subnetting — Formula

```
Hosts per subnet   = 2^(host bits) - 2
Number of subnets  = 2^(subnet bits)
```

**Example:** /24 → 8 host bits → 2^8 - 2 = **254 hosts**

**-2 kyun?** Network address + Broadcast address reserved hote hain.

---

## 6. Important Protocols + Port Numbers

| Protocol | Port | Use |
|---|---|---|
| HTTP | 80 | Web |
| HTTPS | 443 | Secure Web |
| FTP | 20, 21 | File Transfer |
| SSH | 22 | Secure Shell |
| Telnet | 23 | Remote login (insecure) |
| SMTP | 25 | Email send |
| DNS | 53 | Domain to IP |
| DHCP | 67, 68 | IP auto assign |
| POP3 | 110 | Email receive |
| IMAP | 143 | Email receive (better) |
| SNMP | 161 | Network management |
| RDP | 3389 | Remote Desktop |

**Trick:** **"Some Dogs Have Fancy Paws"** → SMTP(25) DNS(53) HTTP(80) FTP(21) POP3(110)

---

## 7. DNS — Domain Name System

```
DNS = Domain Name → IP Address
Recursive Query   = DNS server khud resolve karta hai
Iterative Query   = Client khud har step pe query karta hai
```

**DNS Resolution Order:**
```
Browser Cache → OS Cache → Router → ISP DNS → Root DNS → TLD → Authoritative DNS
```

---

## 8. TCP 3-Way Handshake

```
Client → SYN      → Server
Client ← SYN-ACK  ← Server
Client → ACK       → Server
✅ Connection Established
```

**4-Way Termination:**
```
Client → FIN → Server
Client ← ACK ← Server
Client ← FIN ← Server
Client → ACK → Server
✅ Connection Closed
```

---

## 9. Routing Protocols

| Protocol | Type | Algorithm | Key Point |
|---|---|---|---|
| RIP | Distance Vector | Bellman-Ford | Max 15 hops |
| OSPF | Link State | Dijkstra | Large networks |
| BGP | Path Vector | — | Internet backbone |
| EIGRP | Hybrid | — | Cisco proprietary |

**Trick:**
- RIP = Simple but limited (15 hops max)
- OSPF = Fast convergence, large networks
- BGP = Internet ka backbone protocol

---

## 10. Flow Control vs Congestion Control

| | Flow Control | Congestion Control |
|---|---|---|
| Problem | Receiver overwhelm | Network overwhelm |
| Solution | Sliding Window | TCP Slow Start |
| Layer | Transport | Transport |

**Sliding Window:**
```
Window Size = Amount of data sent without ACK
Go-Back-N  = Error pe sab retransmit
Selective Repeat = Sirf error wala retransmit
```

---

## 11. Network Devices

| Device | Layer | Function |
|---|---|---|
| Hub | Physical (L1) | Broadcast to all |
| Switch | Data Link (L2) | MAC address based forward |
| Router | Network (L3) | IP based routing |
| Bridge | Data Link (L2) | 2 networks connect |
| Gateway | All layers | Protocol convert karta hai |
| Repeater | Physical (L1) | Signal boost karta hai |

**Trick:** Hub = Dumb (broadcast). Switch = Smart (MAC table). Router = Smartest (IP routing).

---

## 12. HTTP Methods

| Method | Use |
|---|---|
| GET | Data fetch karo |
| POST | Data bhejo (create) |
| PUT | Data update karo (replace) |
| PATCH | Partial update |
| DELETE | Data delete karo |

**HTTP Status Codes:**
```
1xx → Informational
2xx → Success (200 OK, 201 Created)
3xx → Redirect (301 Moved, 304 Not Modified)
4xx → Client Error (400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found)
5xx → Server Error (500 Internal, 503 Service Unavailable)
```

---

## 13. Network Topologies

| Topology | Key Point |
|---|---|
| Bus | Single cable, cheap, single point failure |
| Star | Central hub/switch, easy troubleshoot |
| Ring | Token passing, single failure = network down |
| Mesh | Every node connected, expensive, reliable |
| Tree | Hierarchical, scalable |

---

## 14. Most Asked MCQ Facts

- **MAC Address** = 48 bits, hardware address, Data Link layer
- **ARP** = IP → MAC address (same network)
- **RARP** = MAC → IP
- **ICMP** = Error reporting (ping use karta hai)
- **NAT** = Private IP → Public IP translate karta hai
- **Firewall** = Traffic filter karta hai rules ke basis pe
- **VPN** = Encrypted tunnel over public network
- **Bandwidth** = Maximum data transfer capacity
- **Latency** = Delay in data transfer
- **Throughput** = Actual data transferred per second
- **Full Duplex** = Dono direction simultaneously
- **Half Duplex** = Ek time pe ek direction (walkie-talkie)
- **Simplex** = Sirf ek direction (TV broadcast)
- **Checksum** = Error detection technique
- **CRC** = Cyclic Redundancy Check, error detection

---

## Quick Revision Table — Ek Nazar Mein

```
OSI = 7 layers    TCP/IP = 4 layers
TCP = Reliable    UDP = Fast
IPv4 = 32 bit     IPv6 = 128 bit
DNS port = 53     HTTP = 80    HTTPS = 443
Hub = L1          Switch = L2  Router = L3
ARP = IP→MAC      RARP = MAC→IP
```

---

**Teeno subjects done.** DBMS + OS + CN — jo bhi MCQ aaye TCS ya kisi bhi placement mein, in notes se bahar nahi jaayega.
