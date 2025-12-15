# NFL International Market Expansion Strategy
**Data-driven segmentation identifying priority markets for NFL international growth**

## Team
Maria Margarida Sacouto  
Fairfield University - DATA 6560  
December 2025

---

## Problem and Stakeholder

**Problem:** The NFL operates games in 6 international markets but lacks systematic prioritization for future expansion. Which of the remaining 128 eligible countries offer the strongest combination of fan interest, economic capacity, infrastructure, and connectivity to justify strategic investment?

**Decision Impact:** This analysis informs resource allocation for marketing campaigns ($50M+ annually), game placement negotiations, media rights deals, and potential franchise development over the next 3-5 years.

**Stakeholder:** NFL International Strategy & Business Development
---

## Dataset Overview

**Source:** Multi-source integration combining Google Trends API, World Bank indicators, stadium databases (World Of Stadiums dataset), and aviation connectivity metrics (from OpenFlights).

**One Row =** One country with composite scores across four strategic pillars

**Sample Size:** 128 countries after excluding outliers and nations already hosting NFL games

**Key Variables:**
- Fan Interest: Google Trends composite for "NFL," "American football," "Super Bowl"
- Economic Readiness: GDP per capita, population, urbanization rate
- Infrastructure: Stadium count and average capacity
- Connectivity: Airport network strength and international route access

See full dataset in `data/merged_data.csv`

---

## Method and Approach

### Analysis Pipeline

**CP4 - Data Integration & Cleaning:**  
Merged four datasets, handled 47 countries with missing connectivity data, removed 7 outlier/existing markets, validated 128 final observations

**CP5 - Exploratory Analysis:**  
Discovered strong correlation between GDP and infrastructure (r=0.72), identified Canada-China-France as preliminary leaders through univariate rankings

**CP6 - Market Attractiveness Index (MAI):**  
Constructed composite index with equal 25% weights across four pillars, normalized all variables 0-1 via Min-Max scaling. Applied k-means (k=4) to segment markets into strategic tiers, validated with silhouette analysis and PCA visualization. 

**CP7 - K-Means Clustering:**  
Improved index weight distribution. Ran simulations with randomized weights to confirm top market robustness.

---

## Key Results
![Market Attractiveness Heatmap](figures/CP8_Key_Exhibit.png)
### Headline Finding
**Canada dominates all expansion scenarios** with MAI score of 0.596 and 97% top-10 stability across weight variations. The "Magnificent Six" (Canada, China, France, Mexico, Australia, Netherlands) consistently outperform on all four pillars.



### Top 10 Priority Markets

| Rank | Country | MAI Score | Stability |
|------|---------|-----------|-----------|
| 1 | Canada | 0.596 | 97.3% 
| 2 | China | 0.518 | 93.3% 
| 3 | France | 0.435 | 87.0% 
| 4 | Mexico | 0.421 | 62.7% 
| 5 | Australia | 0.400 | 90.7%
| 6 | Netherlands | 0.372 | 77.0%
| 7 | Qatar | 0.363 | 72.0% 
| 8 | UAE | 0.340 | 40.3%
| 9 | Austria | 0.340 | 49.7%
| 10 | Singapore | 0.334 | 38.0%

**Strategic Takeaway:** Canada merits franchise feasibility study for quick expansion.

---

## How to View or Reproduce

### Quick Start
1. **Review Analysis:** Open `reports/Margarida_Sacouto_CP6.pdf` and `reports/Margarida_Sacouto_CP7.pdf`for analysis walkthrough
2. **Explore Data:** Navigate to `/data/clean/merged_data.csv` 
3. **Check Analysis Code:** Navigate to `project/DATA6560 - CP6.ipynb` and `data/DATA6560 - CP7.ipynb` for the analysis code


### Full Reproduction (Python + Jupyter)
**Requirements:**
- Python 3.8+
- Packages: pandas, numpy, scikit-learn, matplotlib, seaborn
- Google Colab (optional) or Jupyter Notebook

**Steps:**
1. Clone repository: `git clone [your-repo-url]`
2. Install dependencies: `pip install -r requirements.txt` and download merged dataset 
3. Open `/project_notes/DATA6560-CP6.ipynb` `/project_notes/DATA6560-CP7.ipynb` in Jupyter/Colab
4. Run all cells in sequence (change file path to where you stored the file)
5. Outputs will regenerate figures in `/figures/` 

**Data Access:**
- Full dataset: `/data/clean/merged_data.csv`
- Raw sources documented in `data/Raw datasets-20251124T210115Z-1-001.zip`

---

## Repository Map

📁 **`/data`**
- `raw/` - Original Google Trends, World Bank, stadium, aviation CSVs with source links
- `clean/` - Final merged dataset (128 countries), cluster assignments, data dictionary

📁 **`/reports`**
- `Margarida_Sacouto_CP2` - Question and problem framing. Initial Analysis Proposal
- `Margarida_Sacouto_CP3.pdf` - Source identification and data strategy
- `Margarida_Sacouto_CP4.docx` - Integration process and quality checks
- `Margarida_Sacouto_CP5.pdf` - Univariate distributions and correlation analysis
- `Margarida_Sacouto_CP6.pdf` - Index methodology and equal-weight rationale, K-means segmentation
- `Margarida_Sacouto_CP7.pdf` - Finetuning and improvements
- `Margarida_Sacouto_CP8.pdf` - **Start here** - Complete findings and recommendations

📁 **`/figures`**
All figures used in CP reports.

📁 **`/project_notes`**
All notebooks with data pipeline and analysis

📄 **`README.md`** - This file


---

## Limitations and Next Steps

### Current Limitations
1. **Static Measurement:** MAI uses static data; markets like China (COVID recovery) or Middle East (Qatar, Dubai) (infrastructure investment) may shift rapidly
2. **Missing Data:** +40 countries excluded due to data gaps
3. **Google Trends Proxy:** Fan interest metric may underweight non-English search behavior or piracy-heavy markets

### Next Steps (Priority Order)
1. Validate fan interest via NFL Game Pass subscriptions and merchandise sales by country
2. Annual MAI refresh with updated economic/connectivity data; flag >20% movements in any pillar
3. Perform Canada expansion feasibility study leveraging Toronto market depth

---

## Acknowledgments

**Instructor:** Professor Gadze, Fairfield University, DATA 6560

**Data Sources:**
- Google Trends API (Fan Interest)
- World Bank Open Data (GDP, Population, Urbanization)
- Stadium Database Project (Infrastructure)
- OpenFlights/OAG (Aviation Connectivity)

**Tools:** Python 3.10, scikit-learn 1.6, Google Colab, GitHub

**Inspiration:** NFL's plans for expansion: https://www.nfl.com/news/roger-goodell-discusses-expanding-international-slate-to-asia-has-no-doubt-nfl-s-dublin-game-will-be-successful

