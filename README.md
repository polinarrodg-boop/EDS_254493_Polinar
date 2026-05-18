# 🐟 AQU-04: Automated Telemetry Ingestion and Nitrification Efficiency Diagnostics for Recirculating Aquaculture Systems

> An object-oriented data engineering architecture designed to synchronize decoupled IoT sensor streams, isolate operational chemistry thresholds, and compute bio-filter kinetic stability.

---

## 👤 Student Profile

| :--- | :--- |
| **Student Nmae** | `[ Rodg Polinar ]` |
| **Student ID No.** | `[ TUPM-25-4493 ]` |
| **Course, Year, and Section** | BSECE – 1C |
| **Subject** | Computer Programming 1 |
| **Professor** | Engr. Gilfred Allen Madrigal |
| **University** | Technological University of the Philippines – Manila |

---

## 🌱 Purpose of this Project

Maintaining water quality parameters within closed Recirculating Aquaculture Systems (RAS) requires continuous mitigation of toxic total nitrogen. This specialized analytics script automates the compilation of multi-stream environmental logs to map biological bio-filter conversion anomalies across varying water chemistry profiles.

**Operational System Tranches:**

| Operational Domain | Environmental pH Scale | Meaning |
| :--- | :--- | :--- |
| 🟢 **Target Operation** | $\ge 7.5$ | Maximum nitrification kinetics; structurally stable |
| 🟡 **System Inhibition** | $7.1 - 7.4$ | Biological activity drop-off; operational drift detected |
| 🔴 **Critical Failure** | $< 7.1$ | Total nitrification arrest; toxic ammonia buildup |

**Primary Analytical Finding:** Restricting data ingestion to the targeted operational boundary of **$\text{pH} \ge 7.5$** establishes an average conversion efficiency index of **88.45%** with highly stable variance characteristics.

---

## 📁 Repository Blueprint

```text
EDS_254493_Polinar/
│
├── main.py                    ← Core compilation program (runs pipeline end-to-end)
├── requirements.txt           ← Declared library environmental manifests
├── README.md                  ← Comprehensive execution documentation
│
├── data/
│   ├── data_original/         (9 unaligned asynchronous raw JSON telemetry streams)
│   │   ├── ph ACTSOR-AQUA-UDC-3.json
│   │   ├── Ammonium ACTSOR-AQUA-UDC-1.json
│   │   └── [Remaining localized parameter logs...]
│   │
│   └── cleaned.csv            (5,871 compiled lines — Target operational slice)
│
└── outputs/                   # Generated engineering visual assets
    ├── static_1_efficiency_distribution.png
    ├── static_2_ammonia_reduction_boxplot.png
    ├── static_3_correlation_heatmap.png
    ├── interactive_1_efficiency_telemetry.html
    └── interactive_2_vulnerability_animation.html
```
---
## 🗄️ Sensor Logging Architecture

The parsing matrix operates on raw, detached internet-of-things (IoT) environmental logs recording parameters across active monitoring nodes.

| Data Domain | File Structure / Volumetric Profile | Substantive Role |
| :--- | :--- | :--- |
| `data_original/*.json` | 9 Disjoint Serialization Vectors | Asynchronous source streams (decoupled intervals) |
| `data/cleaned.csv` | 5,871 Chronological Vectors | **Filtered, aligned, and synchronized analysis source** |

Key runtime variables generated include `Timestamp` 🔑, `pH`, `Temperature`, `Ammonia_Inlet`, `Ammonia_Outlet`, `Dissolved_Oxygen`, and `Filter_Efficiency`.

---

## 🧹 Automated Cleaning Workflow

The compilation layer processes the data through five automated phases:

1. **Stream Discovery:** Ingests isolated JSON log structures, handles metadata exclusions, and standardizes feature column headers.
2. **Nearest-Match Temporal Alignment:** Binds independent records using an asynchronous time join (`pd.merge_asof`) restricted to a 30-second window.
3. **Data Type Normalization:** Coerces inputs to high-precision floats and replaces missing matrix elements with median values.
4. **Boundary Constraint Enforcement:** Executes a logical slice operation to isolate telemetry records matching the **$\text{pH} \ge 7.5$** engineering rule.
5. **Vectorized Mathematical Expansion:** Passes the target arrays to low-overhead arrays to compute final nitrification percentage metrics before exporting the checkpoint file.

---

## 🔬 Statistical Tests

All calculations run via optimized NumPy array operations on the cleaned operational slice.

| Test / Metric | What It Measures | Key Result |
|---|---|---|
| 📊 Descriptive Stats | Mean, median, SD, min/max | Avg filter efficiency ≈ 88.45%, avg temperature ≈ 26.42°C |
| 📈 Dispersion Analysis | System volatility and variance | Temperature variance = 0.84, efficiency variance = 6.74 |
| 🔗 Covariance Matrix | Multivariable alignment correlation | Isolates feature interactions across water chemical states |
| ⚖️ Efficiency Tracking | Intake vs. Discharge performance shifts | Checked using: $\frac{\text{Ammonia}_{\text{Inlet}} - \text{Ammonia}_{\text{Outlet}}}{\text{Ammonia}_{\text{Inlet}}} \times 100$ |

---

## 📊 Outputs

**3 static charts** (distribution histogram, comparative intake vs. discharge boxplot, and matrix heatmap) and **2 interactive assets:**

- 🎞️ `interactive_1_efficiency_telemetry.html` — Dynamic interactive range slider timeline tracking nitrification efficiency chronology over time.
- 🌐 `interactive_2_vulnerability_animation.html` — Cross-sectional scatter frame-by-frame animation showing performance drift over system pH modifications.

---

## ⚙️ How to Run

```bash
# 1. Direct terminal to project directory
cd C:\Users\RODG\OneDrive\Desktop\ComProg_Lab\EDS_254493_Polinar

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run everything
python main.py
```
---

## 📌 Results

| Metric | Value |
|---|---|
| Filter Conversion Efficiency (Mean) | **88.4480%** |
| Filter Conversion Efficiency (Median) | **88.4113%** |
| Target Filter Operational Records | **5,871 Lines** |
| Mean Ammonia Inlet Concentration | 1.5731 mg/L |
| Mean Ammonia Outlet Concentration | 0.1858 mg/L |
| Operational Water Temperature (Mean) | 26.4154°C |

---

## 📦 Dependencies

```text
numpy>=1.24.0
pandas>=2.0.0
matplotlib>=3.7.0
plotly>=5.13.0
