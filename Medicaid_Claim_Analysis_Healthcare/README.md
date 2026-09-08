# Medicare Hospital Spending Analysis by Claim Type

An analytical data pipeline that processes, standardizes, and evaluates Medicare hospital spending data to isolate major cost drivers, profile high-spending healthcare facilities, and calculate variance against national financial benchmarks.

---

## Project Overview & Objectives

This project analyzes episode-based Medicare spending to answer three core operational questions:

1. **Claim Category Cost Ranking:** Which medical claim types generate the highest average spending per episode?
2. **Facility Profiling:** Which healthcare institutions (`facility_id`, `facility_name`) exhibit the highest spending volume nationwide?
3. **National Benchmark Variance:** Which specific hospital claims exceed national average expenditures?

---

##  Data Pipeline & Engineering Steps

The notebook implements a streamlined 4-stage processing workflow:

* **Ingestion & Data Audit:** Ingests `Medicare_Hospital_Spending_by_Claim.csv`, auditing initial schema structure, missing values, and data types.
* **Schema Standardization:** Cleans and normalizes header formats to lowercase `snake_case` for reliable programatic indexing.
* **Type Casting:** Formats temporal fields (`start_date`, `end_date`) into explicit Pandas `datetime64` objects.
* **Feature Engineering & Aggregation:**
  * Aggregates and ranks `avg_spndg_per_ep_hospital` by `claim_type`.
  * Extracts top 10 highest-spending facilities by group aggregation.
  * Engineers a comparative benchmark metric:
    
    $$\text{difference\_vs\_national} = \text{avg\_spndg\_per\_ep\_hospital} - \text{avg\_spndg\_per\_ep\_national}$$

---

## Calculated Outputs & Key Metrics

* **`claim_type` Cost Ranking:** Ranked distribution of average episode expenditure across claim categories.
* **Top 10 High-Cost Facilities:** Isolated facility list ranked by highest mean episode expenditure.
* **Financial Variance Column:** `difference_vs_national` feature flagging over-performance or under-performance relative to national averages.
