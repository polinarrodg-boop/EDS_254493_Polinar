# 🐟 AQU-04 — Bio-Filter Efficiency Tracking in Recirculating Aquaculture Systems

> An automated Python pipeline that isolates the exact water chemistry thresholds where bio-filter nitrification efficiency drops—and validates the system drift using vectorized NumPy analytics.

---

## 👤 Student Info

| | |
|---|---|
| **Student Name** | `[ Rodg Polinar ]` |
| **Student Number** | `[ TUPM-25-4493 ]` |
| **Course & Section** | BSECE – 1C |
| **Subject** | Computer Programming 1 |
| **Professor** | Engr. Gilfred Allen Madrigal |
| **School** | Technological University of the Philippines – Manila |

---

## 🌱 What This Project Does

Recirculating Aquaculture Systems (RAS) require strict ammonia management. High ammonia levels = toxic environment for aquatic life. This pipeline processes asynchronous IoT sensor telemetry to isolate bio-filter conversion performance boundaries based on system water chemistry.

**Three zones, clearly defined:**

| Zone | pH Level | Meaning |
|---|---|---|
| 🟢 **Optimal Operation** | $\ge 7.5$ | Target range — high bacterial nitrification kinetic efficiency |
| 🟡 **Sub-Optimal Drift** | $7.1 - 7.4$ | Inhibited biological activity, track telemetry closely |
| 🔴 **Critical Stress** | $< 7.1$ | Severe nitrification arrest, dangerous toxic ammonia accumulation |

**Core finding:** Filtering operations to the engineered boundary of **$\text{pH} \ge 7.5$** stabilizes the system, yielding an average biological conversion efficiency rate of **88.45%** with minimal variance.

---

## 📁 File Structure

```text
EDS_254493_Polinar/
│
├── main.py                    ← Run this — does everything automatically
├── requirements.txt
├── README.md
│
├── data/
│   ├── data_original/         (9 separate multi-stream raw IoT JSON logs)
│   │   ├── ph ACTSOR-AQUA-UDC-3.json
│   │   ├── Ammonium ACTSOR-AQUA-UDC-1.json
│   │   └── [Other raw telemetry streams...]
│   │
│   └── cleaned.csv            (5,871 rows — Filtered operational checkpoint)
│
└── outputs/
    ├── static_1_efficiency_distribution.png
    ├── static_2_ammonia_reduction_boxplot.png
    ├── static_3_correlation_heatmap.png
    ├── interactive_1_efficiency_telemetry.html
    └── interactive_2_vulnerability_animation.html
```

---
## 🗄️ The Dataset

The pipeline processes multi-stream IoT sensor nodes recording decentralized telemetry from independent tracking stations.

| Dataset | Format / Rows | Purpose |
|---|---|---|
| `data_original/*.json` | 9 Log Streams | Asynchronous raw source data — unaligned |
| `data/cleaned.csv` | 5,871 Rows | **The actual analysis source (pH $\ge$ 7.5)** |

Key columns generated include `Timestamp` 🔑 (the index variable), `pH`, `Temperature`, `Ammonia_Inlet`, `Ammonia_Outlet`, `Dissolved_Oxygen`, and `Filter_Efficiency` — all aligned timeseries telemetry.

---

## 🧹 How Data Gets Cleaned

Five steps, run automatically in sequence:

1. **Parse Telemetry Nodes** — Read disjoint JSON files, cast parameters, and normalize headers.
2. **Asynchronous Alignment** — Execute a temporal nearest-match join (`pd.merge_asof`) across a 30,000 ms window to fix decoupled tracking intervals.
3. **Coerce Numerics & Impute** — Cast parameters to numerical values and fill missing indices using feature medians.
4. **Enforce Engineering Boundary** — Programmatically filter the active dataset to isolate operations where **$\text{pH} \ge 7.5$**.
5. **Compute Kinetic Vectors** — Transform arrays to calculate final bio-filter nitrification conversion metrics into an updated check-pointed `.csv`.

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
---

## 📌 Key Results at a Glance

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
