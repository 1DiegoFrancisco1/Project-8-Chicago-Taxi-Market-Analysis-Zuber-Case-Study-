# 🚕 Project 8 — Chicago Taxi Market Analysis (Zuber Case Study)

### 🏙️ Project Context
You work as a data analyst for **Zuber**, a ridesharing company operating in Chicago.  
The business goal is to **analyze demand patterns**, identify **top-performing neighborhoods**,  
and test whether **weather conditions affect trip durations** on key routes.  

This analysis combines **SQL queries** and **Python EDA** to extract insights and validate hypotheses.

---

## 📂 Datasets

| File | Description |
|-------|-------------|
| `project_sql_result_01.csv` | Taxi companies and number of trips on Nov 15–16, 2017. |
| `project_sql_result_04.csv` | Average daily number of trips per neighborhood in Nov 2017. |
| `project_sql_result_07.csv` | Trip data from the Loop to O’Hare Airport, including weather and duration. |

---

## 🧹 Step 1 — Data Loading and Inspection
- Imported all CSVs using **Pandas**.
- Checked for missing values, duplicates, and corrected data types (e.g., dates as `datetime`).
- Verified column consistency and descriptive statistics.

---

## 📊 Step 2 — Exploratory Data Analysis

### 🚖 Top Taxi Companies by Trips
Bar chart comparing trip counts per company for Nov 15–16, 2017.

**Findings:**
- Trip volume is **highly concentrated** — a few large operators dominate the market.
- Smaller companies contribute marginally to total demand.
- Indicates **market oligopoly**, typical of major U.S. cities.

---

### 🏙️ Top 10 Drop-off Neighborhoods
Bar chart showing neighborhoods with the highest average daily trips in November 2017.

**Key Insights:**
- The **top 4 neighborhoods** (all within Downtown) account for **over 41,000 daily trips** combined.  
- **O’Hare** ranks 5th, reflecting the importance of **airport transfers**.  
- From rank 6–10, demand drops sharply to ~1,200–2,400 trips/day; beyond that, many areas fall below 500.  

📍 **Implication:**  
Concentrating driver allocation in these high-demand zones could improve fleet utilization.

---

### 🕓 Travel Patterns
- **Weekday rush hours:** Loop and West Loop dominate during commuting times.  
- **Leisure hours:** River North and Streeterville attract more evening and weekend rides.  

---

## 💡 Business Insights for Zuber

1. **Geographic Prioritization:**  
   - Concentrate drivers in **Loop–River North** during peak hours.  
   - Maintain a dedicated **“corridor” to O’Hare Airport** to capture travel-to-airport demand.  

2. **Dynamic Pricing:**  
   - Apply **surge pricing** in lower-demand neighborhoods (outside Top-10) to encourage drivers and balance supply.

---

## 🧪 Step 3 — Hypothesis Testing  
### 🎯 Hypothesis  
> “The average trip duration from the Loop to O’Hare International Airport changes on rainy Saturdays.”

| Symbol | Mathematical Formulation | Interpretation |
|:--------|:-------------------------|:----------------|
| **H₀** | μ<sub>rainy</sub> = μ<sub>clear</sub> | Mean trip duration does **not** change on rainy Saturdays. |
| **H₁** | μ<sub>rainy</sub> ≠ μ<sub>clear</sub> | Mean trip duration **does** change when it rains. |

---

### 🧮 Test Setup
- **Test Used:** Welch’s t-test for independent samples  
  *Different sample sizes and variances → Welch correction applied.*
- **Variable:** Trip duration (in seconds)
- **Significance Level:** α = 0.05  
- **Decision Rule:** Reject H₀ if *p-value < α*

---

### 📈 Results
✅ **p-value < 0.05 → Reject H₀**  
There is **strong evidence** that average trip durations differ between rainy and clear Saturdays.

| Condition | Mean Duration (min) | Difference |
|------------|---------------------|-------------|
| ☀️ Clear | 33.3 | — |
| 🌧️ Rainy | 40.5 | +7.2 (+21%) |

🧭 **Interpretation:**  
Rain increases average travel time by ~21%.  
For **operational planning**, this means Zuber should:
- Adjust **pickup time estimates** under rainy conditions.
- Integrate **weather-based pricing** or scheduling algorithms for high-impact routes (like Loop → O’Hare).

---

## 🧠 Conclusion

- **Demand is ultraconcentrated** in Downtown Chicago; the top 5 neighborhoods dominate drop-off activity.
- **O’Hare Airport** remains a strategic destination with consistent daily volume.
- **Rain significantly impacts trip duration**, validating the importance of real-time weather adjustments.

**Strategic Impact:**  
By integrating geographic and weather-based insights, Zuber can:
- Optimize **driver allocation**.
- Improve **ETA accuracy**.
- Enhance **customer satisfaction** and **fleet efficiency**.

---

## 🧰 Tools and Libraries
- **Python:** Pandas, NumPy, Matplotlib, Seaborn, SciPy  
- **Statistical Testing:** `ttest_ind` (Welch’s correction)
- **SQL Integration:** Extracted and cleaned queries from PostgreSQL database
- **Visualization:** Bar charts, histograms, and distribution plots

---

## 🧾 Deliverables
- Cleaned, merged datasets of Chicago trip data.  
- EDA visualizations highlighting demand concentration.  
- Statistical test confirming weather’s effect on travel duration.  
- Actionable business recommendations for fleet and pricing strategy.

---

## 👨‍💻 Author
**Diego Francisco Domínguez Aguilar**  
_Data Science Bootcamp – TripleTen (2025)_  
