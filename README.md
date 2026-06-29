# Intelligent Network Inventory and Capacity Planning System

A data-driven system that transforms raw network infrastructure data into actionable insights — tracking device inventory, monitoring utilization trends, forecasting future capacity needs, and storing everything in a structured MySQL database through an interactive Power BI dashboard.

---

## Problem Statement

Network administrators often rely on manual spreadsheets to track hundreds of devices across multiple locations — making it difficult to spot utilization bottlenecks, identify expired warranties, or plan for future infrastructure growth. This system automates that process end-to-end.

---

## Solution Overview

This project ingests network inventory and utilization data, processes it through a Python-based analytics pipeline, stores it in a MySQL database, and surfaces insights through a 3-page interactive Power BI dashboard — enabling proactive decision-making rather than reactive firefighting.

---

## Tech Stack

| Layer | Tools |
|---|---|
| Data Processing | Python, Pandas, NumPy |
| Visualization (EDA) | Matplotlib, Seaborn |
| Notebooks | Jupyter Notebook (Anaconda) |
| Database | MySQL, SQLAlchemy, PyMySQL |
| Dashboard | Power BI Desktop |
| Version Control | Git, GitHub |

---

## Project Structure

```
intelligent-network-capacity-system/
│
├── data/
│   ├── raw/                        # Original inventory data (Excel)
│   └── processed/                  # Cleaned CSVs and chart exports
│
├── notebooks/
│   ├── 01_data_preprocessing.ipynb
│   ├── 02_inventory_analysis.ipynb
│   ├── 03_trend_analysis.ipynb
│   └── 04_capacity_forecasting.ipynb
│
├── scripts/
│   └── db_loader.ipynb             # MySQL database loader script
│
├── dashboard/
│   └── network_capacity_dashboard.pbix
│
├── docs/                           # Project proposal
├── requirements.txt
└── README.md
```

---

## Project Phases

### Phase 1 — Data Preprocessing
- Loaded 85 network devices across 3 data tables (Asset Inventory, Utilization Records, Growth History)
- Validated data quality: zero missing values, zero duplicates
- Converted date columns to proper datetime format
- Exported clean CSVs for downstream analysis

### Phase 2 — Inventory Analysis
- Breakdown of 85 devices across 5 types and 9 locations
- Identified **52 devices (61%)** with expired warranties requiring urgent attention
- Visualized warranty status distribution by device type and location

### Phase 3 — Trend Analysis
- Analysed 18 months of utilization data (Jan 2025 – Jun 2026) across Bandwidth, CPU, Memory, and Port metrics
- Tracked device growth from 2020–2026 across all device categories
- Access Points identified as the fastest growing device type

### Phase 4 — Capacity Forecasting
- Calculated average yearly growth rates per device type from historical data
- Forecasted device requirements for 2027, 2028, and 2029
- Flagged devices exceeding 75% utilization thresholds across CPU, Memory, and Bandwidth
- Generated actionable upgrade recommendations per device

### Phase 5 — MySQL Integration
- Created a `network_inventory` database in MySQL
- Loaded all 5 cleaned tables into MySQL using SQLAlchemy and PyMySQL:
  - `asset_inventory` — 85 rows
  - `utilization_records` — 1,530 rows
  - `growth_history` — 35 rows
  - `upgrade_recommendations`
  - `forecast_counts`

### Phase 6 — Power BI Dashboard
3-page interactive dashboard:

| Page | Contents |
|---|---|
| Inventory Overview | Device counts, location breakdown, warranty status |
| Utilization Dashboard | 18-month trends, device type comparison, interactive slicer |
| Capacity Planning | Growth forecast, upgrade recommendations table, device slicer |

---

## Key Findings

- **61%** of network devices have expired warranties and require replacement planning
- **Access Points** recorded the highest growth rate since 2020 — driven by campus Wi-Fi expansion
- Multiple devices flagged with **high CPU and Memory utilization** (≥75%) requiring immediate upgrade
- Network is projected to grow significantly by 2029 based on historical growth trends

---

## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/AribAlam-Z/intelligent-network-capacity-system.git
cd intelligent-network-capacity-system
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Run notebooks in order**
```
01_data_preprocessing.ipynb
02_inventory_analysis.ipynb
03_trend_analysis.ipynb
04_capacity_forecasting.ipynb
```

**4. Set up MySQL**

- Install MySQL Server and create a database:
```sql
CREATE DATABASE network_inventory;
```
- Open `scripts/db_loader.ipynb` and update the connection string with your credentials:
```python
from urllib.parse import quote_plus
password = quote_plus("your_password")
engine = create_engine(f'mysql+pymysql://root:{password}@localhost:3306/network_inventory')
```
- Run all cells to load data into MySQL

**5. Open the dashboard**

Open `dashboard/network_capacity_dashboard.pbix` in Power BI Desktop.

---

## Database Schema

| Table | Rows | Description |
|---|---|---|
| `asset_inventory` | 85 | All network devices with warranty info |
| `utilization_records` | 1,530 | 18 months of utilization metrics per device |
| `growth_history` | 35 | Year-by-year device counts 2020–2026 |
| `upgrade_recommendations` | varies | Devices flagged for upgrade action |
| `forecast_counts` | 15 | Forecasted device counts 2027–2029 |

---

## Author

**Mohammed Arib Alam**  
Computer Science (Data Analytics) — Asia Pacific University (APU)  
Network Assistant Intern — APU Network Operations Centre (NOC)  

[![GitHub](https://img.shields.io/badge/GitHub-AribAlam--Z-181717?style=flat&logo=github)](https://github.com/AribAlam-Z)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Arib%20Alam-0077B5?style=flat&logo=linkedin)](https://linkedin.com/in/arib-alam)
