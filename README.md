# dynamic-network-topology-visualizer
A full-stack network topology discovery and visualization system that polls SNMP-enabled routers and switches using Go, models network nodes and edges as a graph, exposes topology data through a GraphQL API, and renders a live, interactive network map in the browser using D3.js.

Perfect — now that I can **see the actual files and code style**, I’ll give you a **README that is inspired by what this project really does**, not a generic one.
This will **match the Python SNMP + JSON + D3 frontend workflow** you’re using and still align with *Dynamic Network Topology Visualization*.

You can **directly paste this as README.md**.

---

# Dynamic Network Topology Visualization

This repository contains a network monitoring and visualization system that collects interface statistics from SNMP-enabled devices, processes and stores the data in JSON format, and visualizes network topology and traffic statistics using scalable SVG and D3.js-based frontend experiments.

The project focuses on **practical network data collection, processing, and visualization**, combining backend scripts with frontend graph rendering techniques.

---

## 📌 Project Overview

The goal of this project is to **understand and visualize network behavior** by:

* Collecting interface-level statistics such as input/output octets
* Computing bandwidth usage and utilization over time
* Storing time-series data in structured JSON files
* Rendering network topology and interface statistics using interactive D3.js visualizations

The backend logic simulates or polls SNMP counters, while the frontend reads generated JSON data and displays graphs, links, and topology maps in the browser.

---

## 🧠 Key Capabilities

* Interface traffic monitoring using SNMP-style counters
* Bandwidth and utilization calculation from octet deltas
* Time-series data logging in JSON format
* Frontend experiments for:

  * Scalable SVG rendering
  * Force-directed graphs
  * Colored links and nodes
  * Interactive topology exploration
* Separation of data generation and visualization logic

---

## 🛠️ Technologies Used

### Backend / Data Processing

* **Python**
* **SNMP concepts (ifHCInOctets, ifHCOutOctets, ifSpeed)**
* **JSON-based data storage**
* **LLDP / SNMP notes for topology discovery**

### Frontend / Visualization

* **D3.js**
* **SVG**
* **HTML, CSS, JavaScript**
* **Node.js (for local hosting)**

---

## 📂 Repository Structure

```
.
├── FRONTEND_EXPERIMENTS/
│   ├── scalable_svg/
│   ├── scalable_svg_with_d3/
│   ├── scalable_svg_with_d3_and_force_scale/
│   ├── scalable_svg_with_d3_and_force_scale_and_lines_coloring/
│   ├── JS_line_chart_from_JSON/
│   ├── clickable_lines/
│   └── full_example_html.zip
│
├── html/
│   └── data/
│       └── interface_stats.json
│
├── network_mapper.py        # Core network/interface processing logic
├── graph_json_writer.py     # JSON graph generation
├── helpers.py               # Utility functions (logging, helpers)
├── quicksnmp.py             # SNMP interaction helpers
├── LLDP-MIB.py              # LLDP-related definitions
├── pyconfig.py              # Configuration handling
├── config.ini               # Runtime configuration
├── SNMP_NOTES               # SNMP and LLDP reference notes
├── README.md
└── LICENSE.md
```

---

## ⚙️ How the Backend Works

1. Interface counters (`ifHCInOctets`, `ifHCOutOctets`) are collected or simulated
2. Previous counter values are loaded from `interface_stats.json`
3. Delta values are calculated using timestamps
4. Bandwidth (InSpeed / OutSpeed) is computed
5. Interface utilization is derived using interface speed
6. New values are appended as time-series stats
7. Updated JSON is written back for frontend consumption

This allows the frontend to **render historical and live-like graphs** without tightly coupling to the backend logic.

---

## 📊 Frontend Visualization

The frontend experiments demonstrate:

* Reading JSON-based network data
* Rendering scalable SVG graphs
* Force-directed network layouts
* Color-coded links based on utilization
* Clickable and interactive topology elements

Each experiment folder focuses on **one visualization concept**, making the project suitable for learning and extension.

---

## 🧪 Running the Project

### Backend (Data Generation)

```bash
python network_mapper.py
```

This generates or updates:

```
html/data/interface_stats.json
```

---

### Frontend (Visualization)

You can open the HTML files directly in a browser or host them locally:

```bash
cd html
python -m http.server
```

Then open:

```
http://localhost:8000
```

---

## 🎯 Use Cases

* Network topology visualization
* Interface traffic monitoring
* Learning SNMP counter behavior
* D3.js graph experimentation
* Network engineering education and demos



