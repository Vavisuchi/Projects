# Executive Summary: WA DOH Food Safety Risk & Resource Allocation Audit

---

## 1. Executive Context & Objective
The Washington State Department of Health (WA DOH) oversees food safety and environmental public health across local health jurisdictions (LHJs). However, varying county budgets, staffing levels, and commercial density create significant regional disparities in inspection capacity.

This project built an **automated data analysis pipeline** to evaluate operational capacity, identify severe inspection backlogs, and map public health risk drivers across all Washington county health jurisdictions. The primary objective is to transition state resource allocation from reactive outbreak response to **data-driven, proactive risk mitigation**.

---

## 2. Composite Risk Scoring Framework

> **Composite Risk Score (0–100 Scale)** combines three core weighted operational and epidemiological factors to quantify county risk:

* **Inspection Coverage Deficit (40% Weight):** Measures systemic monitoring gaps in permanent food service establishments.
* **Normalized Backlog Count (30% Weight):** Captures raw volume workload stress (permitted establishments minus actual inspections conducted).
* **Outbreak Severity Index (30% Weight):** Measures active disease outbreak investigations (*Salmonella*, *E. coli*, norovirus).

---

## 3. Strategic Action Matrix

| Risk Tier | Condition | Priority Action Plan | Resource Allocation |
| :--- | :--- | :--- | :--- |
| 🔴 **RED ALERT** | Coverage $< 80\%$ **AND** Outbreaks $\ge 1$ | **DEPLOY EMERGENCY INSPECTORS:** Immediate state audit, deployment of relief inspectors, and active outbreak tracing support. | **Direct State Intervention** |
| 🟡 **YELLOW WARNING** | Backlog $> 30$ kitchens **OR** Coverage $< 85\%$ | **TARGETED STAFFING SUPPORT:** Authorize overtime funding, streamline local inspection scheduling, and reallocate regional staff. | **Targeted Financial & Staffing Support** |
| 🟢 **GREEN** | Operational targets met | **MAINTAIN STANDARD OPERATIONS:** Maintain standard oversight; document and share local operational best practices. | **Standard Oversight** |

---

## 4. Operational Deliverables Generated

1. `output/lhj_risk_summary_report.csv`  
   *Ranked executive dashboard listing all jurisdictions by Composite Risk Score, Risk Tier, and Recommended State Action.*
2. `output/lhj_cleaned_full_dataset.csv`  
   *Normalized data layer containing all cleaned metrics ready for integration into state Tableau dashboards or GIS mapping software.*
