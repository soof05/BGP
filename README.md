```markdown
# 🚀 BADASS — BGP At Doors of Autonomous Systems is Simple  
### 🧠 A Network Simulation Project with Docker, VXLAN, and BGP EVPN

This project was developed as part of the **42 Network / 1337** curriculum. The goal is to simulate and understand core networking technologies like **VXLAN**, **BGP**, **OSPF**, and **EVPN** using real router daemons inside **Docker containers**, orchestrated through **GNS3**.

It is divided into three mandatory parts, each exploring deeper networking scenarios — from building router images with Docker, to tunneling with VXLANs, and finally discovering route reflection and EVPN with BGP.

---

## 📁 Project Structure

| Folder    | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `P1/`     | GNS3 setup with custom Docker images simulating a host and a router.       |
| `P2/`     | VXLAN configuration in both static and dynamic multicast modes.            |
| `P3/`     | BGP EVPN setup with VXLAN 10 and route reflection simulating a datacenter. |
| `README.md` | This file, describing the overall structure and configuration.           |

---

## 🧱 Part 1: GNS3 Configuration with Docker

You will build **two Docker images**:

- **host_<login>**: Based on Alpine Linux with BusyBox, acts as a lightweight client.
- **router_<login>**: Based on Debian, includes Quagga routing suite with BGPD, OSPFD, IS-ISD, and Zebra.

### 🐋 Docker Image Overview

| Image            | Base     | Tools & Services                              |
|------------------|----------|-----------------------------------------------|
| `host_<login>`   | Alpine   | `busybox`, `iproute2`, `iputils`              |
| `router_<login>` | Debian   | `quagga`, `bgpd`, `ospfd`, `isisd`, `zebra`   |

These images are then imported into GNS3 as Docker containers, and connected to test routing behavior.

### 🖥️ Sample Topology

```

\[host\_<login>] <----> \[router\_<login>]

````

All files (Dockerfiles, configs, exported project) are placed inside the `P1/` folder.  
GNS3 project is exported with base images as a `.zip`.

---

## 🌐 Part 2: Discovering VXLAN

This part introduces **VXLAN (Virtual eXtensible LAN)** using two approaches:

- **Static VXLAN**: Configured with bridge and vxlan interfaces
- **Dynamic VXLAN (Multicast)**: Uses a multicast group (e.g., `239.1.1.1`) for dynamic group communication

### 🔧 Key Configuration Concepts

- Create VXLAN interfaces (`vxlan10`)
- Attach to bridges (`br0`)
- Assign Ethernet interfaces to the bridge
- Test connectivity via ping between endpoints
- Use `bridge fdb show` to inspect MAC learning

All configuration files and the exported GNS3 project are included in the `P2/` folder.

---

## 📡 Part 3: Discovering BGP with EVPN

In this final part, you simulate a **datacenter-like environment** using:

- **BGP EVPN** (RFC 7432) without MPLS
- **VXLAN ID 10**
- **Route Reflector (RR)** as a central controller
- **Dynamic MAC discovery**

### 🏗️ Goals

- Each VTEP (virtual tunnel endpoint) is a router connected to one or more hosts.
- Hosts can communicate through BGP-learned VXLAN tunnels even without assigned IP addresses.
- MAC routes (type 2) are dynamically discovered through EVPN.

### 🕸️ BGP EVPN Concepts Covered

- VNI (VXLAN Network Identifier)
- Route Types: 2 (MAC/IP advertisement), 3 (Inclusive Multicast Route)
- Route Distinguisher (RD), Route Target (RT)
- Leaf-Spine topology with RR in center

The full topology and config files are found in the `P3/` folder.

---

## 📦 Export Instructions

For each part, the GNS3 project must be exported as `.zip`:

```bash
# In GNS3:
File → Export portable project → Include base Docker images
````

Exported ZIPs (`P1_export.zip`, etc.) must be included in each folder:

* `P1/`
* `P2/`
* `P3/`

---

## 📌 Naming Rules

* All devices, images, and files must include your login (e.g. `host_habibi`, `router_habibi`).
* No IP addresses should be preconfigured inside the Docker images.
* All configuration files must include comments explaining their purpose.

---

## ✅ Evaluation Checklist

| Requirement                                | Status |
| ------------------------------------------ | ------ |
| Docker images created and documented       | ✅      |
| GNS3 containers imported and running       | ✅      |
| VXLAN static and multicast tested          | ✅      |
| BGP EVPN with dynamic MAC learning working | ✅      |
| Project zipped and committed               | ✅      |

---

## 📚 Concepts Practiced

* Dockerfile creation and container networking
* GNS3 simulation with custom images
* Routing protocols: OSPF, BGP, IS-IS
* VXLAN tunneling (static and multicast)
* BGP EVPN with route reflection
* MAC address learning and L2 virtualization

---

## 🧠 Author

* 👤 Mohammed Habibi Ihlane , Zakaria walad , Soufiane El Ouafqaoui
* 🏫 1337 / 42 Network
* 📅 2025

---

## 🌐 Final Thoughts

This project is a deep dive into software-defined networking principles, preparing you for real-world infrastructure automation, cloud networking, and advanced protocol deployment. If you’ve reached this far — congratulations, you’re officially a BADASS. 😎🔥
