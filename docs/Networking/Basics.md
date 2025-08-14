# Basic 👻

### 🖧 Local Area Network (LAN) – Refresher Notes

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

## 🔍 Difference: Switch vs Router

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

## ✅ Quick Summary
- **LAN** = local area communication
- **Topologies** = layout of devices
- **Switch** = smart hub for LAN
- **Router** = gateway between networks
# 🌐 Subnetting – Refresher Notes

## 📌 What is Subnetting?
Subnetting is the process of dividing a larger network into **smaller, manageable sub-networks (subnets)**.

> 💡 **Analogy**: Think of subnetting like slicing a cake. The whole network is the cake, and each department or section of the organization gets a slice.

---

## 🏢 Example Use Case: Office Departments
- **Accounting**
- **Finance**
- **HR**

Each department can be placed in its **own subnet**, ensuring organized communication and better control.

---

## 🔢 Subnetting Uses IP Addresses for 3 Key Roles

| **Type**            | **Purpose**                                              | **Example**          |
|---------------------|----------------------------------------------------------|----------------------|
| Network Address      | Identifies the start of the network                      | `192.168.1.0`        |
| Host Address         | Identifies individual devices within the network         | `192.168.1.100`      |
| Default Gateway      | Forwards traffic to other networks (outside the subnet)  | `192.168.1.254`      |
## 🧠 IP Address + Subnet Mask Basics
- An **IP address** has 4 octets (e.g., `192.168.1.100`)
- A **subnet mask** also has 4 octets and determines how many hosts a subnet can have
- Common subnet masks:
  - `/24` → 255.255.255.0 (up to 254 hosts)
  - `/25` → 255.255.255.128 (126 hosts)
  - `/30` → 255.255.255.252 (2 hosts)

---

## 💡 Why Subnet?

### ✅ Benefits of Subnetting:
- **Efficiency**: Reduces broadcast domains, saves IP space
- **Security**: Isolates devices from each other (e.g., employees vs guests)
- **Control**: Easier to manage specific network segments

---

## ☕ Example: Café Setup
The café might have 2 subnets:
1. **Staff Subnet**: POS systems, staff devices, printers
2. **Public Subnet**: Customer Wi-Fi

This keeps the public traffic **isolated** from the private systems.

---

## 📚 Summary
- Subnetting splits large networks into smaller ones
- Helps organize devices by role or department
- Increases network **efficiency, security, and control**
- Involves **network address**, **host address**, and **default gateway**

# 🧠 Address Resolution Protocol (ARP)

## 📝 Summary
ARP (Address Resolution Protocol) is a network protocol used to map an IP address (logical identifier) to a MAC address (physical identifier) within a local network.

---

## 🔧 Purpose
- Enables communication between devices on a LAN by resolving IP addresses to MAC addresses.
- Maintains an **ARP Cache** to remember previously resolved addresses.

---

## 📦 How ARP Works

### 1. **ARP Cache**
- Each device stores a **local table (cache)** mapping IP addresses to MAC addresses.
- Helps avoid sending unnecessary requests repeatedly.

---

### 2. **ARP Request**
- Broadcast sent to the entire network.
- Asks: **"Who has this IP address? Tell me your MAC."**

---

### 3. **ARP Reply**
- The device that owns the IP responds with its MAC address.
- Only the correct device replies; others ignore the request.

---

## 🔄 ARP Message Types

| Type        | Description                                       |
|-------------|---------------------------------------------------|
| ARP Request | "Who owns IP x.x.x.x?" (Broadcast)               |
| ARP Reply   | "I do. Here is my MAC address: xx:xx:xx:xx"      |

---

## 📌 Example Flow

1. Device A wants to talk to IP `192.168.1.5`.
2. Sends **ARP Request**: "Who has `192.168.1.5`?"
3. Device B replies: "I do, MAC is `00:11:22:33:44:55`"
4. Device A updates its **ARP Cache**.

---

## 🛠 Key Concepts

- **MAC Address** = Hardware address (physical)
- **IP Address** = Network-level address (logical)
- **ARP Cache** = Stored mappings of IP ↔ MAC
- **Broadcast** = Sent to all devices on the LAN

---

## 🔐 Security Note
- ARP can be **spoofed** (e.g., ARP Poisoning), which is used in MITM attacks.
---
# 🌐 DHCP & IP Address Assignment – Refresher Notes

## 📌 What is DHCP?
**DHCP (Dynamic Host Configuration Protocol)** is a network protocol used to **automatically assign IP addresses** and other network settings to devices on a network.

---

## 🧠 Methods of IP Address Assignment

### 1. **Manual (Static) Assignment**
- IP address is configured **manually** by the user or admin
- Usually used for servers, printers, routers, etc.
- Example: `192.168.1.10` manually set on a printer

### 2. **Automatic (Dynamic) Assignment via DHCP**
- Most common method
- **DHCP server** dynamically assigns IP addresses to devices

---

## 🔄 DHCP Process (4-Step Handshake)

| **Step**             | **Name**          | **Purpose**                                                                 |
|----------------------|-------------------|------------------------------------------------------------------------------|
| 1️⃣ DHCP Discover     | Broadcast by the client to find a DHCP server                                           |
| 2️⃣ DHCP Offer        | DHCP server responds with an available IP address offer                                |
| 3️⃣ DHCP Request      | Client sends a request to accept the offered IP address                                |
| 4️⃣ DHCP Acknowledgment (ACK) | DHCP server confirms the lease and assigns the IP to the device               |
## 📦 What Info Does DHCP Provide?
- IP Address (e.g., `192.168.1.101`)
- Subnet Mask (e.g., `255.255.255.0`)
- Default Gateway (e.g., `192.168.1.1`)
- DNS Server(s)

---

## 🛠️ Benefits of DHCP
- **No manual setup** for each device
- Reduces IP conflicts
- Easy network scaling and management

---

## 💡 Fun Fact
If no DHCP server is found, Windows devices may auto-assign a **169.254.x.x** IP → this is called **APIPA** (Automatic Private IP Addressing), and it only allows **local communication**.

---

## 📚 Summary
- DHCP automates IP address assignment
- Uses a 4-step handshake: Discover → Offer → Request → ACK
- Reduces admin overhead and ensures network consistency


> Always apply these frameworks with **threat intelligence, logging, and SIEM integration** for effective detection and response.


[github](https://github.com/AyushCodezz/Cyber_notes.git)
