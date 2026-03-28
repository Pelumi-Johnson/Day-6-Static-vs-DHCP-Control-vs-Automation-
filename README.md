# 🖧 Day 6 | Static vs DHCP (Control vs Automation)

## 🎯 Objective
Understand when to use DHCP, when to use static IP addressing, and why real networks often use both together.

---

## 🧠 Core Idea
Not every device should receive its identity dynamically.

Some devices need stable, predictable addressing so they can always be found on the network.

This lab focused on the difference between automatic addressing and manual control.

---

## 🌐 DHCP vs Static IP

### DHCP (Dynamic)
DHCP assigns IP addresses automatically.

Commonly used for:
- PCs
- phones
- guest devices
- general client systems

Benefits:
- fast deployment
- easier management
- reduced manual configuration

### Static IP (Manual)
Static addressing is configured manually.

Commonly used for:
- routers
- servers
- printers
- infrastructure devices

Benefits:
- stable addressing
- predictable communication
- easier long-term reference

![DHCP vs Static Overview](https://github.com/Pelumi-Johnson/Day-6-Static-vs-DHCP-Control-vs-Automation-/blob/main/Screenshot%202026-03-28%20121759.png)

---

## 🧠 Analogy
- DHCP = hotel room assignment
- Static IP = home address

DHCP gives identity when needed.
Static IP stays fixed and predictable.

---

## 🧪 Lab Setup
Rebuilt the network from memory using:
- 1 Router
- 1 Switch
- 2 PCs

![Network Topology](https://github.com/Pelumi-Johnson/Day-6-Static-vs-DHCP-Control-vs-Automation-/blob/main/Screenshot%202026-03-28%20112555.png)

---

## ⚙️ DHCP Configuration on Router

Configured the router as a DHCP server:

enable  
configure terminal  

ip dhcp pool NETWORKPOOL  
network 192.168.1.0 255.255.255.0  
default-router 192.168.1.1  
dns-server 8.8.8.8  
exit  

interface gigabitEthernet 0/0  
ip address 192.168.1.1 255.255.255.0  
no shutdown  

![Router DHCP Config](https://github.com/Pelumi-Johnson/Day-6-Static-vs-DHCP-Control-vs-Automation-/blob/main/Screenshot%202026-03-28%20112930.png)

---

## 🖥️ Mixed Addressing Configuration

### PC0 → DHCP
Configured PC0 to receive its IP address automatically through DHCP.

![PC0 DHCP Assignment](https://github.com/Pelumi-Johnson/Day-6-Static-vs-DHCP-Control-vs-Automation-/blob/main/Screenshot%202026-03-28%20112942.png)

---

### PC1 → Static IP
Configured PC1 manually with:

- IP Address: 192.168.1.50
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.1.1

![PC1 Static Configuration](https://github.com/Pelumi-Johnson/Day-6-Static-vs-DHCP-Control-vs-Automation-/blob/main/Screenshot%202026-03-28%20113123.png)

---

## 📡 Connectivity Test

From PC0:

ping 192.168.1.50

Communication was successful because both devices were in the same network and correctly configured.

![Successful Ping Test](https://github.com/Pelumi-Johnson/Day-6-Static-vs-DHCP-Control-vs-Automation-/blob/main/Screenshot%202026-03-28%20113205.png)

---

## 💥 Failure Scenario

Changed PC1 static IP to:
192.168.2.50

This moved the device into a different network.

As a result, communication failed because:
- PC0 remained in 192.168.1.x
- PC1 was now in 192.168.2.x

### 📸 Insert Screenshot Here
![Failed Ping Test](ping-failure.png)

---

## What This Lab Showed
This lab demonstrated a real-world network scenario where:
- some devices receive addresses automatically
- some devices use permanent manual addressing

This is common in enterprise environments because different device roles require different levels of flexibility and control.

---

## Key Concepts Learned
- DHCP is useful for automatic IP assignment on end-user devices
- Static IP addressing is important for critical devices that require consistency
- DHCP and static IP addressing can coexist in the same network
- Incorrect static IP configuration can break communication even when DHCP is working
- Engineers use both dynamic and static addressing intentionally based on device role

---

## 🔁 Practical Reinforcement
- Rebuilt the topology from memory
- Configured DHCP on the router
- Assigned one device automatically
- Assigned one device manually
- Tested successful communication
- Broke communication by assigning the wrong static IP
- Diagnosed and understood the failure

---

## ✅ Outcome
Developed a stronger understanding of the difference between dynamic and static IP addressing and how both are used together in real network environments.

This lab reinforced that good network design is not just about making devices connect, but about choosing the right level of automation and control.
