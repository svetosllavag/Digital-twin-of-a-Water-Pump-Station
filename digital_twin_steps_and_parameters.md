# Digital Twin Plan (ArcGIS Pro + ArcGIS Online)

## Goal
Build a digital twin prototype of a water pump station using ArcGIS Pro and ArcGIS Online.

The digital twin will:
- model the pump station assets (pumps, reservoir, pipes, zones)
- store operational data as attributes (status, pressure, flow, energy, runtime)
- provide dashboards for monitoring and decision support
- support scenario-based demonstration of realistic station situations
- optionally integrate sensor telemetry from a mini physical model (Arduino)

This is an operational and decision-support digital twin, not a full hydraulic simulation.

---

## Step 1 — Create the pump station model in ArcGIS Pro

### 1. Create project structure
- ArcGIS Pro project
- File geodatabase

### 2. Create station layers
**Point layers**
- Pumps (3 points: Pump A, Pump B, Pump C)
- Reservoir (1 point)
- Valves (optional)

**Line layers**
- Pipes

**Polygon layers**
- Supply zones (2–5 polygons representing consumer areas)

### 3. Add the digital twin fields (attributes)
Minimum recommended fields:

**Pumps**
- `AssetID`
- `Name`
- `Role` (Primary / Backup)
- `Scenario`
- `Status` (Normal / Warning / Failure)
- `IsActive` (0/1)
- `RuntimeHours`
- `Energy_kWh`
- `EnergyEfficiency_kWh_m3`
- `FlowRate_m3h`
- `Pressure_bar`
- `Timestamp`

**Reservoir**
- `AssetID`
- `Scenario`
- `Status`
- `Level_pct`
- `QualityIndex` (0–100)
- `Timestamp`

**Zones**
- `AssetID`
- `Scenario`
- `ServiceStatus` (OK / Reduced / Outage)
- `DemandLevel` (Low / Normal / High)
- `Pressure_bar`
- `WaterLossRisk` (optional)
- `Timestamp`

---

## Step 2 — Prepare 4 operational scenarios

The prototype includes 4 predefined station scenarios (saved station states):

1. **Normal Operation**
   - Pump A: ON  
   - Pump B: ON  
   - Pump C: OFF (backup)

2. **Backup Exercise (Wear Balancing)**
   - Pump A: OFF  
   - Pump B: ON  
   - Pump C: ON  

3. **Energy Saving Mode**
   - Pump A: ON  
   - Pump B: OFF  
   - Pump C: OFF  

4. **Pump Failure**
   - Pump A: FAILURE  
   - Pump B: ON  
   - Pump C: ON  

Each scenario includes different values for:
- flow rate
- pressure
- energy use
- pump runtime
- zone service status

---

## Step 3 — Visualization in ArcGIS Pro

- Pumps colored by `Status`
- Backup pump visually distinct from primary pumps
- Zones colored by `ServiceStatus` or `Pressure_bar`
- Optional: 3D scene for a digital twin style view

---

## Step 4 — Publish the station to ArcGIS Online

## Step 5 — Create dashboards (ArcGIS Dashboards)

### Dashboard 1 — Station Overview
Purpose: fast control-room view
- total flow indicator
- average pressure indicator
- active pumps count
- scenario label
- map (zones + pumps)

### Dashboard 2 — Pumps & Wear
Purpose: maintenance and wear balancing
- runtime hours per pump (chart)
- energy per pump (chart)
- pump status table
- backup usage indicator

### Dashboard 3 — Energy & Sustainability
Purpose: efficiency and cost awareness
- total energy (kWh)
- energy efficiency (kWh/m³)
- scenario comparison chart
- optional CO₂ proxy

---

## Step 6 — Web app interface (Experience Builder)

Create a simple web app with an “Experiment Control Panel”:
- Normal Operation
- Backup Exercise
- Energy Saving
- Pump Failure

Each button filters by `Scenario` and updates the map and dashboards.

---

## Step 7 (Optional) — Telemetry integration from a mini physical model

A small Arduino-based pump station model can generate real telemetry values (level, current, turbidity).  
Data can be logged to CSV and used in the digital twin for demonstration.

Enterprise-style future options:
- ArcGIS Velocity
- ArcGIS GeoEvent Server
- SCADA export / OPC-UA integration

---

## Final Deliverable
A working pump station digital twin prototype that demonstrates:
- infrastructure asset model
- operational monitoring dashboards
- scenario-based decision support
- future-ready path to real telemetry and SCADA integration
