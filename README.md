# NBA-Workload-Injury-Risk-Analysis  

SQL + Tableau project analyzing NBA player workload and injury risk. This project explores how both **absolute workload (minutes played)** and **relative workload changes (spikes)** contribute to injury likelihood.

---

## Executive Summary  
This project investigates the relationship between **player workload and injury incidence** using a structured SQL data pipeline and Tableau dashboard.

Rather than relying on simple correlations, this analysis:
- Integrates **multi-source datasets (game logs + injury reports)**
- Engineers **player-level workload and injury features**
- Quantifies **injury likelihood across workload tiers**
- Evaluates **both cumulative load and short-term workload changes**

The final output is an analysis-ready dataset and dashboard that supports **injury risk evaluation and load management decisions**.

---

## Problem Statement  
In professional sports, injuries directly impact **team performance, player availability, and long-term health outcomes**.

However, injury risk is not driven solely by high minutes — it is also influenced by:
- Sudden increases in workload  
- Accumulated fatigue over time  
- Repetitive biomechanical stress  

This project aims to answer:

- How does MPG influence injury probability?  
- Are workload spikes more dangerous than sustained high load?  
- Which injury types are most associated with workload stress?  

---

## Dashboard Preview  
<img width="1998" height="1166" alt="NBA Workload" src="https://github.com/user-attachments/assets/9444e99a-2344-4b24-bb89-d55e07bb2f6d" />

---

## Data  

**Time Period:** Multi-season NBA data (~2003–2023)  
**Granularity:** Player-game → Player-season  

### Sources  
- `games` – game metadata (dates, IDs)  
- `games_details` – player minutes and performance  
- `injuries_clean` – cleaned and standardized injury dataset  
- `nba_workload` – aggregated workload metrics  
- `injury_summary` – injury counts and classifications  

---

## Data Processing Pipeline  

### 1. Workload Data Preparation  
- Converted minutes from `"MM:SS"` into numeric format for analysis  
- Created `minutes_clean` field for consistent calculations  
- Aggregated player workload metrics (MPG, total minutes)  

---

### 2. Injury Data Standardization  
- Rebuilt and standardized the injury dataset to ensure consistency across seasons  
- Cleaned player identifiers and aligned injury records with game data  
- Derived season values from injury dates for temporal analysis  

---

### 3. Injury Classification  
- Categorized injuries into body regions (knee, ankle, hamstring, etc.)  
- Used keyword-based logic to standardize unstructured injury descriptions  
- Enabled aggregation and comparison of injury trends across categories  

---

### 4. Feature Engineering  
- Created `injury_flag` (binary indicator of injury occurrence)  
- Calculated `injury_count` per player  
- Grouped players into workload buckets:
  - 0–9.9 MPG  
  - 10–19.9 MPG  
  - 20–29.9 MPG  
  - 30+ MPG  

---

### 5. Data Integration  
- Combined workload and injury datasets using joins  
- Built final dataset: **`master_tableau`**  
- Ensured:
  - No duplicate records  
  - Proper alignment between workload and injury events  

---

## Analytical Approach  

### Workload vs Injury Analysis  
- Compared injury rates across workload tiers  
- Evaluated relationship between **minutes played and injury incidence**  

### Workload Change Analysis  
- Assessed impact of **workload spikes vs stable workload**  
- Categorized workload changes into:
  - Higher Load (Spike)  
  - Normal  
  - Slightly Lower  
  - Much Lower  

---

### Core Concepts Applied  
- Data transformation and cleaning  
- Feature engineering for analytical datasets  
- Dataset integration across multiple sources  
- Aggregation and grouping for insight generation  

---

## Key Results  

- Players with **30+ MPG show ~77% injury rate**  
- **Workload spikes** are associated with increased injury risk  
- Injury rates remain elevated even at moderate workloads (~66–74%)  
- **Knee and ankle injuries are the most frequent**  

---

## Interpretation  

Findings suggest that injury risk is driven by:

### Absolute Load  
Higher sustained minutes increase fatigue and physical stress  

### Relative Load Change  
Sudden workload increases elevate injury likelihood due to insufficient recovery  

---

### Practical Implications  
- Monitor **short-term workload spikes**, not just averages  
- Incorporate **rate of change** into load management strategies  
- Focus on **lower-body injury prevention efforts**  

---

## Dashboard Features  

- KPI metrics (Avg MPG, Injury Rate)  
- Workload vs injury scatter plot  
- Injury type distribution  
- Workload exposure vs injury incidence  
- Injury rate by workload change categories  

---

## Tech Stack  

- **PostgreSQL** – Data extraction, cleaning, transformation  
- **SQL** – Feature engineering, joins, aggregations  
- **Tableau** – Dashboard visualization  

---

## SQL Scripts  
All transformation logic is available in the `/sql` folder for full reproducibility.

---

## Limitations  

- Injury data depends on reporting accuracy  
- Does not yet include:
  - Back-to-back games  
  - Rolling workload windows  
  - Player position or biomechanics  

---

## Future Improvements  

- Add **7-day / 14-day rolling workload metrics**  
- Incorporate **back-to-back game tracking**  
- Build **predictive injury models**  
- Integrate **player tracking or biomechanical data**  

---

## Notes  

- Data compiled from public/synthetic sources for portfolio use  
- Demonstrates an **end-to-end analytics pipeline from raw data to insights**  
