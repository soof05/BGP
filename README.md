```markdown
# BADASS - BGP At Doors of Autonomous Systems is Simple 🧠📡

Welcome to the BADASS project! This repository contains the three main parts of the project which simulate networking environments using **GNS3** and **Docker**. You’ll discover advanced topics such as **VXLAN**, **BGP**, and **EVPN** using real-world routing tools.

---

## 🗂️ Repository Structure

```

BADASS/
├── P1/                # Part 1: GNS3 + Docker setup
│   ├── Dockerfile.host
│   ├── Dockerfile.router
│   ├── zebra.conf
│   ├── bgpd.conf
│   ├── ospfd.conf
│   ├── isisd.conf
│   ├── daemons
│   ├── P1.gns3project
│   └── P1\_export.zip
├── P2/                # Part 2: VXLAN static & multicast
│   ├── P2.gns3project
│   └── VXLAN config files
├── P3/                # Part 3: BGP EVPN with route reflection
│   ├── P3.gns3project
│   └── EVPN config files
└── README.md

```

---

## 🧩 Part 1 - GNS3 Configuration with Docker

### 🔹 Objectives
- Set up two custom Docker images:
  1. **host_<login>**: a minimal host image (Alpine + BusyBox)
  2. **router_<login>**: router image with Zebra/Quagga, BGP, OSPF, IS-IS support
- Integrate both images into GNS3
- Build a test topology:
  
```

+-------------+       +---------------+
\| host\_<login>| <---> | router\_<login>|
+-------------+       +---------------+

```

### 🔧 Key Steps
- Install GNS3 and Docker
- Build Docker images using provided Dockerfiles
- Use GNS3 Preferences → Docker Containers to register your images
- Export the GNS3 project as `.zip` and include it in `P1/`

---

## 🌐 Part 2 - Discovering VXLAN

### 🔹 Objectives
- Understand and simulate **VXLAN** using both:
- Static VXLAN configuration
- Multicast-based VXLAN (dynamic)
- Build a GNS3 topology that uses VXLAN with VNI `10`
- Set up bridges (e.g. `br0`) and Ethernet interfaces between hosts

### 🔧 Configuration Summary
- Create VXLAN interfaces (`vxlan10`)
- Attach them to bridges (`br0`)
- Test connectivity via `ping`
- Verify MAC learning with bridge tools (e.g., `bridge fdb show`)

### 🔁 Dynamic Mode
- Use a multicast group like `239.1.1.1` to simulate dynamic VXLAN
- Confirm that endpoints join and learn dynamically

---

## 🔁 Part 3 - BGP with EVPN

### 🔹 Objectives
- Discover **BGP EVPN** without MPLS
- Use **VXLAN ID 10** again
- Implement **Route Reflection (RR)** and **dynamic MAC discovery**
- Configure multiple VTEPs (virtual tunnel endpoints)

### 🔧 Topology Concepts
- Use OSPF to simplify underlay routing
- Configure BGP with:
- Route Distinguisher (RD)
- Route Target (RT)
- Use GNS3 hosts like: `host_<login>-1`, `host_<login>-3`
- Observe route type 2 auto-generation when MAC addresses are discovered

---

## 💾 Export Instructions

### For each part:
- File > Export portable project
- ✅ Include base images
- Save the project as `.zip` in `P1/`, `P2/`, `P3/`

---

## 📌 Naming Rules & Notes

- All machines and configs **must include your login** (e.g. `host_habibi`, `router_habibi`)
- Do **not** preconfigure IPs inside Docker images
- Add comments inside all config files
- Follow folder naming strictly:
- `P1/`, `P2/`, `P3/` — each must contain the `.gns3project` file and configs

---

## ✅ Submission Check List

| Item                             | Done |
|----------------------------------|------|
| Docker images built correctly    | ✅   |
| Topologies set up in GNS3        | ✅   |
| Config files added and commented | ✅   |
| All parts exported to `.zip`     | ✅   |
| Project folders organized        | ✅   |
| GNS3 nodes named with login      | ✅   |

---

## 🤝 Evaluation Tips

- Be ready to **explain terms** like: VXLAN, BGP, EVPN, RD/RT, Route Reflector, OSPF, MAC learning, etc.
- Your evaluation happens on your machine — test everything twice!
- Use `README.md` to guide the evaluator

---

## 🚀 Authors

- 👤 Name: Mohammed Habibi Ihlane , Zakaria Walad , Soufiane El Ouafqaoui
- 💻 Project: BADASS – 42/1337 Network Simulation
- 📅 Year: 2025

---

## 🧠 Enjoy Routing Like a BADASS!

```
