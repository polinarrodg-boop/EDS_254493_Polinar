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
