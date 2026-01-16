# dynamic-network-topology-visualizer
A full-stack network topology discovery and visualization system that polls SNMP-enabled routers and switches using Go, models network nodes and edges as a graph, exposes topology data through a GraphQL API, and renders a live, interactive network map in the browser using D3.js.
Absolutely! Let’s make this README more **friendly, modern, and visually engaging** by adding emojis, highlighting key sections, and keeping it detailed but approachable. Here’s a polished version:

---

## ✨ Features

1. **📡 Dynamic SNMP Data Collection**

   * Supports SNMP v2c and v3 for fetching device information.
   * Polls individual OIDs, bulk requests, and SNMP tables.
   * Automatically detects LLDP neighbors to discover device connections.

2. **📊 Interface Traffic & Stats Logging**

   * Tracks interface stats (`ifHCInOctets`, `ifHCOutOctets`) for each device interface.
   * Calculates **In/Out speeds**, bandwidth utilization, and records historical stats.
   * Handles counter wrap automatically to prevent incorrect readings.

3. **🗂 JSON-Based Graph Generation**

   * Stores network topology in JSON files: `graph.json`, `interfaces.json`, `interface_stats.json`, `neighborships.json`.
   * Files are automatically updated and read by the frontend for visualization.

4. **💻 Interactive Frontend Visualization**

   * Uses **D3.js** for force-directed, zoomable, and draggable network diagrams.
   * Uses **Plotly.js** to display interface traffic charts over time.
   * Open `full_example_html/index.html` to see your network instantly.

5. **🎨 Customizable Layouts & Optimization**

   * Frontend directories like `01_graphics`, `02_graph_optimization`, and `scalable_svg_with_d3_and_force_scale` allow advanced customization.
   * Supports clickable links, interactive zooming, and hierarchical node layouts.

6. **🛠 Extensible Backend**

   * Python scripts are modular and can be extended for custom SNMP queries or new visualizations.
   * Key scripts:

     * `network_mapper.py` → orchestrates SNMP polling & graph creation
     * `graph_json_writer.py` → writes JSON for frontend
     * `quicksnmp.py` → helper SNMP functions
     * `LLDP-MIB.py` → LLDP neighbor parsing
     * `TopologyModel.py` → organizes network topology data

---

## 📋 Table & Node Definitions

* **SNMP Table OIDs**

  * `sysName_named_oid` → Device hostname
  * `interfaces_table_named_oid` → Interface details (name, speed, MAC, etc.)
  * `lldp_table_named_oid` → Neighbor device info
  * `lldp_local_port_name` → Local interface port

* **Visualization Config**

  * `MAX_STATS_RECORDS = 2016` → Maximum history points for interface stats
  * `LINK_SPEEDS` → Regex mapping interface names to speeds (e.g., `GigabitEthernet → 1 Gbps`)
  * `NODE_HIERARCHY` → Regex mapping device names to hierarchical levels (Access, Distribution, Aggregation)
  * `IGNORED_IFTYPES` → Interfaces ignored in visualization (loopbacks, VLANs)

---

## 📂 Project Structure

```
dynamic-visualizer/
│
├─ Classes/                 # Python classes for topology & data handling
│  └─ TopologyModel.py
├─ Frontend/                # Frontend visualization code
│  ├─ 01_graphics/
│  ├─ 02_graph_optimization/
│  ├─ clickable_lines/
│  ├─ CSS_layout/
│  ├─ JS_line_chart_from_JSON/
│  ├─ scalable_svg/
│  ├─ scalable_svg_with_d3/
│  ├─ scalable_svg_with_d3_and_force_scale/
│  └─ scalable_svg_with_d3_and_force_scale_and_lines/
├─ full_example_html/       # Full working HTML example
│  ├─ data/                 # JSON files for example networks
│  ├─ index.html
│  ├─ perf_test.html
│  ├─ scripts.js
│  ├─ style.css
│  ├─ layout.css
│  └─ background.css
├─ html/                    # Additional HTML templates
├─ config/                  # SNMP configuration (`config.ini`)
├─ pyconfig.py              # Low-level Python settings
├─ network_mapper.py        # Main SNMP & mapping script
├─ graph_json_writer.py     # Generates JSON for frontend
├─ quicksnmp.py             # SNMP helper functions
├─ LLDP-MIB.py              # LLDP parsing
└─ helpers.py               # Utility functions (logging, etc.)
```

---

## 🛠 How It Works

1. **⚙️ Configuration**

   * Edit `config/config.ini` with device SNMP details (IP, community, version).
   * Optional low-level tweaks: `pyconfig.py` (polling intervals, JSON paths, logging).

2. **📡 SNMP Data Collection**

   * `network_mapper.py` polls devices for hostname, interfaces, LLDP neighbors, and counters.
   * Supports SNMP v2c & v3, including authentication and encryption.
   * Automatically handles counter wrapping to prevent data errors.

3. **📊 Interface Statistics Logging**

   * Historical statistics are stored in `interface_stats.json`.
   * Tracks bandwidth utilization, calculates In/Out speeds, and appends new data points.

4. **🌐 Topology & JSON Generation**

   * `TopologyModel.py` organizes devices, links, and interface info.
   * JSON files are used by frontend for visualization.

5. **💻 Frontend Visualization**

   * Open `full_example_html/index.html` to view network graph.
   * Interactive features: drag nodes, zoom, hover details, and Plotly traffic charts.

6. **⏱ Automation**

   * Schedule `network_mapper.py` periodically (cron or Task Scheduler).
   * JSON and visualizations update automatically for real-time monitoring.

---

## ⚡ Installation

```bash
# Install required Python libraries
pip install pysnmp networkx json pprint

# Optional for SNMPv3
pip install pycryptodome
```

---

## 🚀 Usage

1. Configure devices in `config/config.ini`.
2. (Optional) Adjust `pyconfig.py` for intervals, JSON paths, or logging.
3. Run network mapper:

```bash
python network_mapper.py
```

4. Open `full_example_html/index.html` in your browser to visualize the network.
5. Monitor interface traffic using the Plotly charts and JSON stats.

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/21ac1e16-0876-4213-95d7-78b926500a80" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3d00901c-8bcf-4dbc-b2eb-7ae343486a84" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/78ba2a3c-9434-43ae-8f2c-62acc33668dc" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6d620185-cc7c-45ca-87af-8cf110cb101e" />




