# Episode-of-Care Spending Divergence: Interactive Scrollytelling Pipeline

An interactive data pipeline and visual scrollytelling analysis that evaluates how and when hospital episode-of-care spending deviates from state and national benchmarks across distinct care phases.

---

## Analytical Objective & Core Question

**Core Question:** *How does a healthcare facility's episode-of-care spending differ from its state and national benchmarks—and at what phase in the care episode do those cost differences emerge?*

By breaking down Medicare spending into temporal episode phases, this analysis identifies operational cost drivers—specifically distinguishing between index admission costs, pre-admission overhead, and post-discharge post-acute care utilization (e.g., Inpatient Readmissions vs. Skilled Nursing Facilities).

---

## Data Pipeline & Transformation Architecture

The pipeline processes and normalizes Medicare episode spending data using a multi-step analytical workflow:
┌──────────────────────────────────────┐
│  Ingestion & Schema Cleaning         │
│  - Strip column whitespace           │
│  - Convert string metrics & percents │
└──────────────────┬───────────────────┘
│
▼
┌──────────────────────────────────────┐
│  Care Phase Normalization            │
│  - Map raw periods to 4 key phases   │
└──────────────────┬───────────────────┘
│
▼
┌──────────────────────────────────────┐
│  Multi-Level Benchmark Aggregation   │
│  - Sum Hospital, State, & National   │
└──────────────────┬───────────────────┘
│
▼
┌──────────────────────────────────────┐
│  Variance Metric Engineering         │
│  - Absolute & % Diff (vs State/Nat.) │
└──────────────────┬───────────────────┘
│
▼
┌──────────────────────────────────────┐
│  Plotly Visualization Engine         │
│  - Interactive phase & claim charts  │
└──────────────────────────────────────┘


### Key Engineering Steps:
1. **Numeric & Percentage Extraction:** Coerces string-based currency and percentage values (`Percent of Spndg`) into clean float representations, handling missing fields gracefully.
2. **Phase Normalization (`normalize_period`):** Categorizes raw temporal descriptions into standard clinical care phases:
   * **`Before admission`** (Pre-admission diagnostic/ambulatory services)
   * **`Index admission`** (Inpatient stay)
   * **`After discharge`** (Post-acute care / follow-up)
   * **`Complete episode`** (Total episode footprint)
3. **Variance Feature Engineering:** Calculates absolute dollar differentials (`Vs State`, `Vs National`) and percentage variances (`Vs State %`, `Vs National %`) to highlight outlier spending behavior.

---

## Visualization Suite & Interactive Components

Built using **Plotly (`plotly.graph_objects`)** and **IPyWidgets**, the visual storytelling suite includes five tailored charts:

* **Complete Episode Spending:** Evaluates total macro-level hospital performance against state and national benchmarks.
* **Spending Across the Episode:** Grouped bar charts tracking cost trajectory across pre-admission, index admission, and post-discharge phases.
* **Claim-Type Spending Mix:** Horizontal breakdown isolating specific claim types within a selected phase.
* **Cost Divergence Engine:** Zero-centered divergence chart highlighting exactly which claim categories drive spending above/below benchmarks.
* **Post-Discharge Acute Care Deep-Dive:** Targeted comparison focusing on **Inpatient Readmissions vs. Skilled Nursing Facility (SNF)** spending.

---

## Tech Stack
* **Language:** Python 3.9+
* **Data Manipulation:** `pandas`, `numpy`
* **Visualization Engine:** `plotly`, `ipywidgets`
* **Environment:** Jupyter Notebook / Google Colab
