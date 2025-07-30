🧠 NETWORKING – FOUNDATION OF CYBER OPERATIONS

Networking is the art and science of **connecting systems** to exchange data.

🔹 Core Purpose:
To transmit data between systems using physical (cables) or wireless (radio) mediums.

# 🖧 Local Area Network (LAN) – Refresher

## 📌 What is LAN?
- A **Local Area Network (LAN)** is a network that connects computers within a limited area such as a home, office, or building.
- Typically spans a range of **a few meters to a few kilometers**.
- **Privately owned** and managed.

---

## 🧭 LAN Topologies

### 1. **Bus Topology**
- All devices connected to a single backbone cable.
- Cheap, easy to implement.
- Failure in backbone = whole network fails.

### 2. **Star Topology**
- All devices connected to a central **hub or switch**.
- Easy to manage and troubleshoot.
- If central device fails → whole network goes down.

### 3. **Ring Topology**
- Devices connected in a circular path.
- Each device has exactly two neighbors.
- Data travels in one direction (or both in dual-ring).

### 4. **Mesh Topology**
- Every device is connected to every other device.
- High redundancy, very reliable.
- Expensive and complex to set up.

### 5. **Hybrid Topology**
- Combination of two or more topologies (e.g., Star + Bus).
- Flexible and scalable.

---

## 🔁 What is a Switch?
- A **Switch** is a Layer 2 network device (Data Link Layer).
- Connects multiple devices in a **LAN**.
- Uses **MAC addresses** to forward data to the correct destination.
- Learns which device is on which port (via MAC learning).
- More efficient than a hub (which broadcasts blindly).

---

## 🌐 What is a Router?
- A **Router** is a Layer 3 device (Network Layer).
- Connects **different networks** together (e.g., LAN to internet).
- Uses **IP addresses** to forward data packets.
- Can assign IP addresses (DHCP), manage traffic, and provide NAT (Network Address Translation).

---

## 🔍 Switch vs Router Comparison

| Feature              | Switch                        | Router                          |
|----------------------|-------------------------------|----------------------------------|
| Layer                | Layer 2 (Data Link)           | Layer 3 (Network)                |
| Uses                 | MAC Address                   | IP Address                       |
| Purpose              | Connects devices in a LAN     | Connects different networks      |
| Communication        | Within the same network       | Between different networks       |
| Routing Capability   | ❌ No routing                  | ✅ Yes (routes packets)           |
| DHCP Support         | ❌ No (unless Layer 3 switch)  | ✅ Yes (assigns IP addresses)     |
| Internet Access      | ❌ Not directly                | ✅ Provides internet access       |

---

## ✅ Summary
- **LAN** = local area communication
- **Topologies** = layout of devices
- **Switch** = smart hub for LAN
- **Router** = gateway between networks

---

# 🌐 Subnetting – Refresher

## 📌 What is Subnetting?
- Subnetting divides a larger network into **smaller, manageable sub-networks (subnets)**.
- Analogy: Like slicing a cake—each department or section gets a slice.

---

## 🏢 Example Use Case
**Departments as Subnets**:
- Accounting
- Finance
- HR

Each placed in its own subnet for efficiency and security.

---

## 🔢 Key IP Address Roles

| Type             | Purpose                                            | Example            |
|------------------|----------------------------------------------------|--------------------|
| Network Address  | Start of the subnet                                | `192.168.10.0`     |
| Host Address     | Specific device in the subnet                      | `192.168.10.25`    |
| Default Gateway  | Exit point to reach other networks                 | `192.168.10.1`     |

---

## 🧠 IP + Subnet Mask Breakdown
- IP: `192.168.10.25`
- Subnet mask defines the division between **network** and **host**.
- Common masks:
  - `/24` → 255.255.255.0 → 254 hosts
  - `/25` → 255.255.255.128 → 126 hosts
  - `/30` → 255.255.255.252 → 2 hosts

---

## 💡 Why Subnet?

### Benefits:
- **Efficiency**: Reduces broadcast traffic
- **Security**: Segments networks logically
- **Manageability**: Easier control of groups of devices

---

## ☕ Example: Café Setup

- **Staff Subnet**: POS, staff phones, printers
- **Public Subnet**: Customer Wi-Fi

This setup ensures guest traffic can't access sensitive systems.

---

## 📚 Summary
- Subnetting organizes a network into segments
- Improves security, performance, and management
- Involves **network**, **host**, and **gateway** concepts

---

# 🧠 Address Resolution Protocol (ARP)

## 📌 What is ARP?
ARP maps an IP address to a **MAC address** on a local network.

---

## 🎯 ARP Purpose
- Enables devices to talk using MACs by resolving IPs.
- Builds and refers to an **ARP cache** for quick lookups.

---

## 📦 ARP Workflow

### 1. **ARP Cache**
- Local table mapping IP ↔ MAC.
- Prevents repeated requests.

### 2. **ARP Request**
- Broadcast sent: _"Who has 192.168.1.5?"_

### 3. **ARP Reply**
- The correct device replies: _"192.168.1.5 is me, MAC: 00:11:22:33:44:55"_

---

## 🔄 ARP Packet Types

| Type        | Description                         |
|-------------|-------------------------------------|
| Request     | Broadcasts: "Who owns this IP?"     |
| Reply       | Targeted response with MAC address  |

---

## 🔐 Security Implication
- ARP is **stateless** and **unauthenticated**.
- Vulnerable to **ARP Spoofing / Poisoning**, used in **MITM** attacks.

---

## 🧾 Summary
- ARP = Resolve IP ↔ MAC
- Works only within a LAN
- Relies on broadcasts and cached lookups
- Can be exploited if not monitored
