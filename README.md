#  National Agri-Food Supply Chain & Food Desert Accessibility Risk Engine


##  Executive Overview
This project presents an end-to-end analytical data engine built to model subnational crop yield volatility, supply-demand deficits, and socio-geographic food accessibility risks across key agricultural clusters in Pakistan (2021–2026). Engineered using relational datasets, SQL conditional logic, and cloud BI dashboarding in **Google Looker Studio**, this framework serves as a decision-support platform for agribusiness logistics and regional food security planning.

---

## Dashboard Preview

![Agri-Food Risk Dashboard Preview](./02_dashboard/dashboard_preview.png)

> 🔗 **[Click Here to Access the Live Interactive Looker Studio Dashboard](https://datastudio.google.com/reporting/920b3d9a-05e3-4924-b0ad-33ba72ab967a/page/cuk5F)
---

##  Core Methodology & Technical Architecture

### 1. Net Supply Deficit Calculation
Regional structural supply deficits are calculated per crop year and district cluster:
$$\text{Supply Deficit (Tons)} = \text{Estimated Demand (Tons)} - \text{Actual Yield (Tons)}$$

Across the multi-year baseline (2021–2026), total crop yield stands at **166,900 Tons** against an estimated demand of **189,900 Tons**, yielding a cumulative structural deficit of **23,000 Tons**.

### 2. Multi-Tier Spatial Risk Engine (SQL Logic)
To evaluate regional vulnerability, a dynamic tiering index was engineered based on supply shortfalls ($>1,500$ tons), spatial isolation ($>20$ km from distribution hubs), and economic vulnerability ($>40\%$ low-income population):

```sql
CASE 
    WHEN supply_deficit_tons > 1500 AND dist_to_grocery_hub_km > 20 AND low_income_pop_pct > 40 
        THEN 'Critical Food Desert Risk'
    WHEN supply_deficit_tons > 0 
        THEN 'Moderate Supply Vulnerability'
    ELSE 'Stable Access Zone'
END AS food_desert_risk_tier
4. Results & Dashboard Visual Analytics:

Figure 1: Interactive Google Looker Studio Agri-Food Risk Dashboard Overview.

A. Executive KPI Scorecards (Filtered View: Crop Year 2026):

The Looker Studio dashboard primary header presents aggregated metrics for the 2026 crop cycle:

KPI Scorecard Metric	Dashboard Display Value	Exact Mathematical Derivation	Agronomic & Operational Interpretation
supply_deficit_tons	3,300	2,000 (Punjab) + 800 (Sindh) + 500 (KPK)	Total annual shortfall across all three commodity belts.
drought_risk_index	0.39	Average (0.48 + 0.38 + 0.32) / 3 = 0.3933	Favorable baseline climate condition across regional clusters.
dist_to_grocery_hub_km	15.83	Average (11.0 + 20.0 + 16.5) / 3 = 15.833 km	Average last-mile logistics distance to distribution hubs.

(Note: Across the full unfiltered 6-year database, cumulative deficit is 23,000 Tons, mean drought risk is 0.53, and mean distance to grocery hub is 18.5 km).

B. Multi-Year Crop Yield Volatility Trends (2021–2026):

The Looker Studio Time-Series Chart tracks actual annual crop yield trajectories (Tons) across regional clusters:

Crop Year	Punjab North (Wheat)	Sindh Central (Rice)	KPK Valley (Maize)
2021	14,500 Tons	9,800 Tons	6,200 Tons
2022	13,200 Tons	8,900 Tons	5,800 Tons
2023 (Drought Peak)	11,800 Tons (Dip)	7,200 Tons (Dip)	5,100 Tons (Dip)
2024	12,100 Tons	8,100 Tons	5,400 Tons
2025	13,800 Tons	9,100 Tons	6,000 Tons
2026	14,200 Tons	9,400 Tons	6,300 Tons

Figure 2: Multi-Year Crop Yield Trajectory across Regional Clusters (2021–2026).

Key Trend Insights:
• The 2023 Climate Drop: All three regional clusters hit their lowest yield levels in 2023 due to peak drought risk indices (0.82 in Punjab, 0.88 in Sindh, 0.71 in KPK).
• Punjab North (Faisalabad - Wheat): Maintains high production volume (11,800 - 14,500 tons), but faces persistent urban demand growth (15,000 - 16,200 tons), leading to continuous deficit.
• Sindh Central (Sukkur - Rice): Showed severe vulnerability in 2023 (7,200 tons yield vs 9,500 tons demand) with distance to market expanding to 28.5 km and poverty at 52%, triggering Critical Food Desert Risk status.
• KPK Valley (Peshawar - Maize): Demonstrates lower overall volume (5,100 - 6,300 tons), operating under narrow margins with steady recovery toward 2026.

5. Practical Value & Agribusiness Applications:
• Early Warning Logistics Allocation: Flags structural deficit zones early, allowing provincial food departments to redirect grain reserves before market shortages occur.
• Targeted Supply Chain Infrastructure: Helps government planning agencies identify where to construct new wholesale storage centers and distribution hubs based on distance-to-market data (>20km).
• Policy & Social Safety Nets: Provides a multi-dimensional risk index for targeting food subsidy distributions to verified food desert areas.

6. Conclusion:
This project demonstrates how combining relational data engineering with dynamic cloud BI dashboarding in Google Looker Studio converts complex multi-source agricultural datasets into actionable supply chain intelligence. The automated risk classification matrix accurately isolates food desert hotspots, providing a scalable decision-support platform for climate-smart agribusiness logistics and regional food security policy.

7. Project Deliverables & Interactive Links:
• Live Interactive Dashboard: https://datastudio.google.com/reporting/920b3d9a-05e3-4924-b0ad-33ba72ab967a/page/cuk5F
• Dataset Source: agri_food_supply_chain_data.csv
