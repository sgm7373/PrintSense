# DOE-Driven Print Quality Analysis for SLA Systems

A computational R&D study that applies Design of Experiments (DOE) and statistical sensitivity analysis to evaluate how SLA print parameters drive part quality, reliability, and throughput. Built to demonstrate R&D engineering thinking — structured experimentation, physics-informed modeling, and data-backed recommendations.

---

## The Problem

When developing or improving an SLA printing process, engineers need to know which parameters actually move the needle on print quality. Running every combination physically is expensive — real resin, real machine time, real engineer hours. A 3-parameter study with 3 levels each means 27 physical prints just to get started.

This study replaces that brute-force physical testing with a structured computational approach: define the parameter space, model the physics, run the experiment, and extract actionable insights.

---

## What This Study Covers

**Parameters evaluated:**
| Parameter | Range | Unit |
|---|---|---|
| Layer Height | 25 / 50 / 100 | µm |
| Exposure Time | 80 / 120 / 160 | ms |
| Support Density | 20 / 50 / 80 | % |

**Output metrics tracked:**
| Metric | Direction |
|---|---|
| Dimensional Accuracy | Lower = better |
| Surface Roughness (Ra) | Lower = better |
| Layer Adhesion Score | Higher = better |
| Print Time | Lower = better |
| Delamination Risk | Lower = better |

---

## Key Findings

**1. Layer Height is the dominant parameter across all metrics.**
- r = 0.912 with Dimensional Accuracy (STRONG, p < 0.05)
- r = 0.946 with Surface Roughness Ra (STRONG, p < 0.05)
- r = -0.908 with Print Time (STRONG, p < 0.05)

Reducing layer height from 100µm → 25µm significantly improves accuracy and surface finish but increases print time by ~4x. This is the primary engineering trade-off.

**2. Exposure Time is the key lever for reliability.**
- r = -0.520 with Delamination Risk (STRONG, p < 0.05)
- r = 0.421 with Layer Adhesion (MODERATE, p < 0.05)

Increasing exposure from 80ms → 160ms reduces delamination risk and improves inter-layer bonding with minimal impact on print time. Best ROI parameter for reliability gains.

**3. Support Density shows weak influence on all metrics.**
No statistically significant correlation detected (p > 0.05) across all output metrics. Support density should be driven by geometry complexity, not print quality targets.

---

## Recommended Configurations

**High Accuracy** (medical, dental, engineering parts)
- Layer Height: 25 µm | Exposure Time: 120–160 ms | Support Density: 50%
- Expected: <15 µm accuracy | Ra < 1.5 | Delamination Risk < 5%

**High Throughput** (prototyping, iteration, volume runs)
- Layer Height: 100 µm | Exposure Time: 120 ms | Support Density: 20–50%
- Expected: ~40 µm accuracy | Ra ~5 | 3–4x faster print time

---

## Visualizations

**Parameter Sensitivity — Correlation Matrix & Influence Chart:**

![Sensitivity Analysis](assets/sensitivity_analysis.png)

**Quality vs Speed Trade-off Analysis:**

![Trade-off Analysis](assets/tradeoff_analysis.png)

---

## How It Works

1. **Parameter Definition** — Defines three key SLA print parameters and their operating ranges based on real printer specifications.

2. **Full Factorial DOE** — Generates all 27 combinations of parameter levels systematically — the standard approach for structured engineering experimentation.

3. **Physics-Informed Data Generation** — Each output metric is modeled using real SLA physics relationships: layer staircase effect on roughness, cure depth driving adhesion, peel force influencing delamination risk. Experimental noise is added to simulate real measurement variability.

4. **Sensitivity Analysis** — Pearson correlation quantifies how strongly each parameter drives each metric, with significance testing to separate real effects from noise.

5. **Trade-off Visualization** — Scatter plots show the quality-speed tension across all 27 runs, color-coded by layer height to make the dominant parameter immediately visible.

6. **Engineering Report** — Final output structured as an R&D deliverable — findings, recommended configurations, and suggested next steps for physical validation.

---

## Suggested Next Steps (for physical validation)

- Validate synthetic model against real print measurements
- Expand DOE to include resin type as a 4th parameter
- Investigate interaction effects between Layer Height and Exposure Time at boundary conditions
- Run focused study at 50µm — data suggests it may offer the best quality-speed balance

---

## How to Run

Open directly in Google Colab — no setup needed.

1. Open `DOE_Driven_Print_Quality_Analysis_for_SLA_Systems.ipynb`
2. Click **Runtime → Run All**
3. All outputs, charts, and the final report generate automatically

---

## Tech Stack

- Python 3, NumPy, Pandas, SciPy, Matplotlib, Seaborn

---

## Project Structure

```
PrintSense/
│
├── DOE_Driven_Print_Quality_Analysis_for_SLA_Systems.ipynb
├── README.md
└── assets/
    ├── sensitivity_analysis.png
    └── tradeoff_analysis.png
```

---

## Author

**Sourabh Gopinath More**
MS Computer Science — Oregon State University
[LinkedIn](https://linkedin.com) | [Portfolio](https://portfolio.com) | [GitHub](https://github.com)
