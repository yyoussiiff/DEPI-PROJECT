# 🛡️ VLAN & Inter-VLAN Routing with FortiGate

## 📌 Project Overview

This project demonstrates the implementation of **network segmentation using VLANs** and **Inter-VLAN routing** within a fully virtualized environment. The architecture utilizes a **Cisco Layer 2 Switch** for VLAN tagging and a **FortiGate Firewall** as the gateway to handle:

* Inter-VLAN Routing
* DHCP Services
* Firewall Security Policies
* Internet Access Control

The primary goal was to **isolate Windows and Linux environments into separate broadcast domains** while still allowing **controlled internal communication and secure internet access** through the firewall.

---

## 👥 Team Members (Group A)

* **Noureen Khaled 21043876**
* **Mariam Abdou 21069532**
* **Youssef Alaa 21092776**
* **Omar Abdrabo 21051923**
* **Karim Khaled 21081010**
* **Ahmed Zaher 21090718**

---

## 🛠️ Technologies & Tools

* **GNS3** – Network Emulation Platform
* **FortiGate VM (v7.0.5)** – Routing, DHCP, and Firewall Policies
* **Cisco Switch (Layer 2)** – VLAN Creation & 802.1Q Trunking
* **Virtual Machines**

  * Windows 10 / Windows 7
  * Ubuntu / Kali Linux

---

## 📐 Network Topology

The network consists of two main VLANs connected via a **single trunk link** to a FortiGate Firewall using a **Router-on-a-Stick** design.

| VLAN ID | Name    | Subnet          | Gateway      | OS Type       |
| ------: | ------- | --------------- | ------------ | ------------- |
|  **10** | Windows | 192.168.10.0/24 | 192.168.10.1 | Windows 10/7  |
|  **20** | Linux   | 192.168.20.0/24 | 192.168.20.1 | Ubuntu / Kali |

---

## ⚙️ Configuration Details

### 🔹 1. Switch Configuration (Layer 2)

* **VLAN Creation:**

  * VLAN 10 → Windows
  * VLAN 20 → Linux
* **Access Ports:**

  * `e0/1`, `e0/2` → VLAN 10
  * `e0/3`, `e1/0` → VLAN 20
* **Trunk Port:**

  * `e0/0` configured as **802.1Q trunk** to carry both VLANs to the FortiGate.

---

### 🔹 2. FortiGate Configuration (Layer 3)

* **Sub-Interfaces:**

  * VLAN 10 and VLAN 20 were created as **sub-interfaces on physical `port2`**.
* **DHCP Services:**

  * DHCP servers enabled on both VLAN interfaces to assign IP addresses automatically to all devices.

---

### 🔹 3. Security Policies (Firewall Rules)

The following firewall policies were implemented:

#### ✅ Internet Access

* **VLAN10 → WAN** → Allowed
* **VLAN20 → WAN** → Allowed

#### 🔄 Inter-VLAN Routing

* **VLAN10 → VLAN20** → Allowed
* **VLAN20 → VLAN10** → Allowed
  ✅ Bi-directional communication was successfully verified.

---

## 🧪 Verification & Testing

* ✅ **Inter-VLAN Connectivity:**

  * Verified using `ping` between Windows and Linux machines across VLANs.
* ✅ **Internet Access:**

  * Tested successfully using web browsers and speed tests.
* ✅ **Traffic Monitoring:**

  * FortiGate logs confirmed correct policy matching and ICMP traffic flow.

---

## 📂 Repository Contents

* 📁 **[GNS3 Topology](gns3/topology.gns3)**
* 📄 **[Project Report](report/final-report.pdf)**
* 📊 **[Project Presentation](presentation/final-presentation.pdf)**
* 🎥 **[Video Demonstration](media/project-demo.mp4)**
* 🧾 **[FortiGate Configuration](configuration/fortigate-running-config.conf)**
* 🧾 **[Switch Configuration](configuration/switch-running-config.txt)**

---

## 🎓 Course Information

**Project completed for Course:** `DEPI Fortinet ONL3_ISS8_S3`.

